`<diamond-child-process-spawn` is a 'native'(Runs in Electron) web component.
It utilizes node's [childProcess](https://nodejs.org/api/child_process.html#child_process_child_process_spawn_command_args_options) to run a childProcess.

### Example:
    
## Running a jar
    
```
<diamond-child-process-spawn
            exec="java"
            args="['-Xmx1024M', '-jar', {{jarPath}}]"
            on-data-recieved="_onDataRecieved"
            on-child-connected="_onChildConnected"
            on-child-process-done="_onChildProcessDone"
            on-process-invalid="_onFailedToConnect"
            on-child-error="_onChildError"
            on-child-disconnected="_onChildDisconnected"
          ></diamond-child-process-spawn>
```
...

```
          _onDataRecieved: function () {
            console.log('[spawn] done!');
          },
          _onChildConnected: function (err) {
            console.error('[spawn] ERROR: ', err);
          },
          _onChildProcessDone: function (data) {
            console.log('_childProcessOnData: ', data.toString());
          },
          _onFailedToConnect: function (data) {
            console.error('_childProcessOnError: ', data.toString());
          },
          _onChildError: function () {
            console.log('detachChildProcess: ');
          },
          _onChildDisconnected: function () {
            console.log('detachChildProcess: ');
          }
```

## Running a system command

```
<diamond-child-process-spawn
            exec="ls"
            args="['-lh', '/usr']"
            on-data-recieved="_onData"
            on-child-connected="_onConnected"
            on-child-process-done="_onData"
            on-process-invalid="_onFailedToConnect"
            on-child-error="_onError"
            on-child-disconnected="_onDisconnected"
          ></diamond-child-process-spawn>
```
