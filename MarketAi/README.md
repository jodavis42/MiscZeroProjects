# AI Steering  

## Description  
AI Steering allows you to create and combine arbitrary AI steering behaviours (ex: wander, flee, avoid, seek, etc).  

## Getting Started  
Download and open the included sample levels. These demonstrate individual behaviours, as well as different combinations.  
There are multiple example behaviours included:  

- Flee  
- Pursue  
- Flee  
- Evade  
- Wander  
- Avoidance  

## Writing Your Own Behaviours  
There are only 2 scripts that make up the core of the steering system:  

- **SteeringComponent** - Base class for all steering behaviours.  
- **SteeringAccumulator** - Root component that all steering behaviours give their results to (move this direction, look this direction). It adds them all up, along with each component's associated weight, creating a weighted average of movement and look vectors.  

First, open these scripts and read the "Brief" at the top of the file. Then open up one of the example behaviour components (seek), and see how it derives and implements SteeringComponent's virtual functions. Then lastly, write your own! Just create your own logic, and give your results to **SteeringComponent's** functions **AddLocalMovement(...)**, **AddWorldMovement(...)**, and **AddLookDirection(...)**.  

## Moving Your Agent  
The **SteeringAccumulator** dispatches an event each frame containing the resulting world/local movement and look direction. Listen to this event, and do what you want with the results. There are example scripts included that do this:  

- SteeringRigidBodyMover - Moves a RigidBody with impulses.  
- SteeringTransformMover - Manipulates a Transform.  
