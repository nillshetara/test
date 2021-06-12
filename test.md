### Available channel and events
|Channel | description | available event|
|---|----|---|
|job.{jobId}|Get job update related event|` job_started`  ` job_failed` `job_completed` |
|task.{taskId}| Task related all event |`task_started` `task_completed` `task_failed` `task_min_update`|
|user.{userId}.jobs|User job releted event|` job_started`  ` job_failed` `job_completed` |
|user.{userId}.tasks|User task releted event|`task_started` `task_completed` `task_failed` `task_min_update`|
### Code Example
```javascript
const socket = io("https://notification.freeconvert.com", {
    transports: ['websocket'],
    path: "/socket.io"
    auth: {
      `token`
    }
});
//for subscribe job and task
socket.emit("subscribe", `job.{jobId}`);
socket.emit("subscribe", `task.{taskId}`);

//for unsubscribe job and task
socket.emit("unsubscribe", `job.{jobId}`);
socket.emit("unsubscribe", `task.{taskId}`);

socket.on("task_started", (data) => {
    console.log("task_started", data);
});

socket.on("job_started", (data) => {
    console.log("job_started", data);
});
```
