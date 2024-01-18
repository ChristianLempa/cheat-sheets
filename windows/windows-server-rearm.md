# Windows Server Evaluation Rearm

Windows Server Evaluations are valid for 180 days. After that period, the server will need to be rearmed a few times. This is useful for testing purposes, and extending the evaluation period for additional 180 days.

## View Windows Server Evaluation Status

```powershell
slmgr /dlv
```

## Rearm Windows Server Evaluation

```powershell
slmgr /rearm
```

Confirm the rearm was successful by running `slmgr /dlv` again.
