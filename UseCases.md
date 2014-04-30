# ROS-Industrial Consortium Roadmapping

# Use Case Document
*note items in _italics_ are suggested specifications for review.

## Purpose
This document is an interim result of a "customer" requirements elicitation process.  It documents end-user needs and application requirements at a high-level for further analysis and breakdown into technical specifications and gap analysis.

## Scope
The scope has been limited to potential ROS-Industrial end-user needs and does not directly address developer, integrator or other stakeholders needs.  It is prioritized based on feedback from current ROS-Industrial Consortium members, but may be revised as additional members join the consortium and additional user needs are identified.

## Use Cases

### 1. CMM-Accelerated Path Planning

__Stakeholder:__ Any user with need to generate accurate path programming from an existing workpiece

__Scope:__ Path based processes such as dispensing, painting, sanding, machining, routing

__Description:__ The operator uses a device such as a portable CMM or motion tracking wand to outline a Cartesian path on a part or tool.  Generally, 6 degree of freedom (DOF) pose information is require to be extracted from the teaching device.  The system then extracts this data and automatically generates robot programming that meets the process constraints and is guaranteed to be executable and collision free.  The proposed path plan is shown in simulation for the operator to approve and then executed.

__Success Criteria:__

* Rapid programming: < 20 minutes 
* Collision free paths: < 0 collisions
* High success rate planning: > _95% successful plans generated_
* Follows existing process specifications (speeds, normalcy etc.)
  
__Technology Areas:__

* CMM Driver to extract high resolution pose data
* Cartesian path filtering
* Constraint-obeying path planning (inverse kinematics)
* Collision checking integrated into IK solution
* Visual (kinematic) simulation
* Operator friendly GUI or wizard interface
	
### 2. Mobile Material Handling

__Stakeholder:__ Any manufacturer or warehouser with significant and repetitive material handling needs between machines or operations

__Scope:__ Material Handling

__Description:__ A manufacturer has material transport needs over distances greater than a few meters.  Examples include machine tending, work-in-progress (WIP) transport, warehousing, order fulfillment etc.  The robot manipulator is on a mobile base and is able to navigate between predefined stations in a dynamic environment.  Other robots, people, or equipment may be in the nominal path, requiring replanning or, minimally, waiting for a clear path.  Once at a destination, the robot is capable of roughly localizing with the machine, shelf, bin etc.  A perception system is capable of recognizing the object(s) of interest in an unstructured presentation such as a bin, shelf, or machine.  Automated path planning and grasp planning permits the robot to pick the object and transport it to the drop-off location (or store onboard for multiple items).  The robot should be capable of reacting automatically to machine or inventory states.

__Success Criteria:__

* Highly reliable: _< 1 human intervention per hour_
* Cost effective: _capital costs < $100k per system_
* Efficient: _< 2X time required for manual process_
* Flexible: able to handle a variety of parts with minimal programming and configuration
  
__Technology Areas:__

* Mobile localization (3DOF: X-Y-Yaw)
* Mobile planning in a known map with obstacles
* Machine/shelf/structure localization (6DOF)
* Cluttered scene 3D mapping
* Object recognition/pose estimation in clutter
* Manipulator planning in cluttered environment
* Grasp planing with clutter/uncertainty
* Adaptable grippers
* Omni directional bases
* Low cost, high dexterity manipulators
* Human safe designs, considering ISO 10218 | RIA R15.06

### 3. Heavy Helper

__Stakeholder:__ Manufacturers with large/heavy objects to be transported or fixtured

__Scope:__ Material Handling

__Description:__ A manufacturer has material transport needs or part fixturing needs that are too large for safe manual operation, i.e. > 50 pounds or awkward to handle.  The operator instead uses a (potentially mobile) robotic manipulator under guided operation to pick and position the part.  The part may be immediately dropped off or positioned for further operation such as welding, painting, or inspection.  The robot is flexible enough to pick a range of parts of similar class.  The user interface may be a direct guided operation or perhaps via a non-contact method such as a gesture command.

__Success Criteria:__

* Flexible: able to handle a variety of parts with minimal programming and configuration
* Easy to command: only non-programming interfaces required
* Cost efficient: minimal capital investment beyond robot cost
* Minimal setup: no cages or other safety equipment, minimal or no calibration
  
__Technology Areas:__

* Gesture or command recognition (optional)
* Guidance sensor (force etc.)
* Gravity compensation
* Adaptable grippers
* Omni directional bases (optional)
* Human safe designs, considering ISO 10218 | RIA R15.06

### 4. Scan 'n' Weld

__Stakeholder:__ Large Weldment Manufacturers

__Scope:__ Welding

__Description:__ Large article welding often requires multiple passes to adequately fill a weld joint and often the large parts have significant geometric distortions either from fabrication tolerances or from thermal deformation.  Current practice for seam tracking can only accomodate small dimensional variations and generally can not adapt to the as-welded condition.  Future systems will sense the condition of the base and weld materials, and they will automatically adjust for both minor deviations such as seam/weld tracking, but also large deviations that might require extra weld passes.  A fully adaptive system could fill an unknown gap or joint without prescribed path plans, only rough joint geometry and the required end conditions.

__Success Criteria:__

* Flexible: No significant programming for new welds other than specifying joint to weld and the desired end conditions
* High Quality: Joint quality equivalent or better than traditionally programmed welds
* Minimal setup: Minimal or no part registration
  
__Technology Areas:__

* Weld process controller
* Automated part registation
* Weld joint sensing
* Constraint-obeying path planning (inverse kinematics)
* Collision checking integrated into IK solution
* Cluttered environment path planning

### 5. Human Collaborative Assembly

__Stakeholder:__ High Volume Assembled Goods Manufacturers

__Scope:__ Assembly

__Description:__ Traditional high volume assembly such as consumer electronics and automotive final assembly are mostly manual operations due to the complex environments, many varied tasks, and high-dexterity operations.  Future robotic assembly capabilities will enable collaborative or shared-space operations where humans would perform high value tasks such as quality control and robots would do repetitive and ergonomically difficult tasks.  The robots would be required to safely and productively work in the same space as the human workers.  The robots would perform multiple assembly operations using adaptable tooling.  Perception capabilities would eliminate issues with work piece registration and cell calibration.  Initial systems would manage light-weight, slow-speed tasks, while future systems would safely handle larger payloads at higher speeds.  The robots will require flexible and intuitive programming so that they can be easily moved and retasked.

__Success Criteria:__

* Flexible: Robots are able to perform a variety of force-guided assembly tasks with a single hardware configuration
* Minimal setup: Minimal or no part registration
* Simple Tooling Design: _Tooling design and fabricated in hours for < $1000_
* Simple Programming: Line operator able to retask
* Cost Effective: Return on investment < 18 months
  
__Technology Areas:__

* Human safe designs, considering ISO 10218 | RIA R15.06 and future standards
* Automated part registation
* Collision checking
* Cluttered environment path planning
* Human pose tracking
* High fidelity force/impedance control

### 6. Machine Tool Blending

__Stakeholder:__ Machined Part Manufacturers

__Scope:__ Material Removal

__Description:__ Machined parts leave small tooling marks that are often undesirable for to aesthetic or surface quality reasons.  Current practice is to manually blend the tool marks with sanding, grinding, or other processes.  A robotic system is needed that has the flexibility to deal with a wide variety of parts and surface conditions.  Fixturing must be simple and flexible between parts.  Robot programming should be intuitive such that the operator only selects the regions to be blended.  The system will have the ability to automatically inspect the result and modulate the process based on the surface state feedback.

__Success Criteria:__

* Flexible: Tooling and robot programming need to be able to handle a wide variety of parts
* Minimal setup: Minimal or no part registration
* Simple Programming: Line operator should be able to "program" a new part
* Coverage: Needs to be able to process _80% of a typical CNC output_
  
__Technology Areas:__

* Automated part registation
* Collision checking
* Cluttered environment path planning
* Constraint obeying path planning
* Machined surfaces sensing/characterization
* GUI interface for selecting surfaces
* Point cloud processing to extract surfaces

### 7. Speed Optimized Path Planner

__Stakeholder:__ Manufacturer/Product Developers with High Speed Material Handling Needs

__Scope:__ Material Handling

__Description:__ A generalized path planner is envisioned for speed-optimized path planning that obeys Cartesian constraints.  A robotic system is needed that provides optimal or near optimal path plans for high DOF systems (6/7 axis articulated arms) that perform material handling tasks.  For example, a fluid container handing robot may need to obey Cartesian constraints to keep the container near vertical while moving in free-space.  More sophisticated constraint models are envisioned, for example that would take into account the dynamics of the fluid in the container to achieve greater accelerations/speeds.  The planning needs to be real-time to account for dynamic replanning.

__Success Criteria:__

* High Performance: plans that are near the theoretical speed (acceleration) of the machine while obeying the constraints
* Fast Planning: _< 1 second plan time_
* Flexible: Able to accomodate multiple serial kinematic configurations including redundant ones 
  
__Technology Areas:__

* Collision checking
* Cluttered environment path planning
* Optimal path planning with constraints
