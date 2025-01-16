# Beginning Of Frame
## WaitForEndOfFrame (Coroutine)
- Handle received network messages
# Physics Update
## FixedUpdate
- Update synced physics transforms
- Character Controller Updates
- Held Physics pickup resets to last frames stored position
- Scripting FixedUpdate
#### Unity Internal Physics
## AnimationJob
- Interpolate and apply remote player muscle values
## WaitForFixedUpdate (Coroutine)
# Frame Update
## Update
- Update synced kinematic transforms
- Scripting Update
## LateUpdate
- OpenVR pose updates
- VRIK updates
- Get and reapply muscle values to avatar for a network pass
- Sync current muscle values outbound
- Held Physics pickup stores current position then moves to hand
- Scripting LateUpdate