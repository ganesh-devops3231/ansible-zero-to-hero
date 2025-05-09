# Error Handling Notes:

### Execution process of Tasks:
- A task executes on each VM in a order, that means if 2 tasks are available then once 1 task is executed across hosts once it is done
  then it moves to next task.
- So, here if any task gets failed for any VM/hosts then other tasks will not be executed for that VM. But for other hosts the execution
  wont stops.
- In this scenario, if it requires to handle the errors that means even any task fails in on host but to proceed other tasks execution in that
  host, in ansible there is a concept called Error Handling.
- To achieve error handling use below syntax in the task, also same script is available in yaml file of this folder:
  ```
  ignore_errors: yes
  ```

  ### Defining Failure:
  - To condition a error message and ignore if that particular error message comes up.
  - 
