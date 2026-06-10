# GAME PROGRAMMING - EX - 7

## EXP - 7 Implement the AI chasing when AI see the player


## Aim:
To create an AI character in Unreal Engine that roams randomly within a NavMesh area and chases

## STEPS

1. Setup Navigation
Add a NavMeshBoundsVolume to your level and scale it to cover the roamable area.
Press P to confirm the green nav area is visible (indicating navigable space).

2. Create AI Character
Create a Blueprint character (e.g., BP_AIEnemy ) with a skeletal mesh and AIController class.
Create an AI Controller Blueprint (e.g., BP_AIController ) and assign it to the character.

3. Enable AI Perception
In BP_AIController , add an AIPerception component.
Configure a Sight sense (set detection range, lose sight range, peripheral vision angle).
Bind OnPerceptionUpdated to update a blackboard value
(e.g., CanSeePlayer and PlayerActor ).

4. Set Up Blackboard
Create a Blackboard with the following keys:
TargetLocation (Vector)
PlayerActor (Object)
CanSeePlayer (Bool)

5. Create Behavior Tree (BT_AI)
Structure it like this:
AI Random Roam with Chase - Unreal Engine. Aim Root, Selector, Sequence (Chase Player)

## Procedure

1. Blackboard Check: CanSeePlayer == truTask: Find Random Location → TargetLocation. Move To: TargetLocation

2. Custom Task: Find Random Location - Create a new BTTask_BlueprintBase to get a random reachable point using: Set the result to the TargetLocation blackboard key.

3. Test the AI - Add a player character to the level. Place the AI enemy in the map and assign its controller and behavior tree.

4. Press Play: the AI should roam when the player is far and chase the player when within sight. UNavigationSystemV1::GetRandomReachablePointInRadius()

## Output

<img width="1919" height="1023" alt="op1" src="https://github.com/user-attachments/assets/bc875582-2cf9-4b37-987a-6085bc164f1c" />

<img width="1919" height="1017" alt="op2" src="https://github.com/user-attachments/assets/dec611b1-3e5b-4872-9609-848dd1118489" />

<img width="1016" height="428" alt="op3" src="https://github.com/user-attachments/assets/76c7e6e9-0712-4505-b842-76bac667fd23" />

<img width="1297" height="498" alt="op4" src="https://github.com/user-attachments/assets/01d199d2-3fa1-4a65-97b0-b91836bcca11" />

## Result
The AI character roams randomly within a defined area. When the player enters its sight range, the AI stops roaming and begins to chase the player until the player is out of sight, after which it resumes roaming.
