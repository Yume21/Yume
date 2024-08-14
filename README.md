import bpy

# Function to create a simple robot
def create_robot():
    # Create the body
    bpy.ops.mesh.primitive_cube_add(size=1.0, location=(0, 0, 1))
    body = bpy.context.object
    body.name = 'RobotBody'
    
    # Create the head
    bpy.ops.mesh.primitive_uv_sphere_add(radius=0.5, location=(0, 0, 2.5))
    head = bpy.context.object
    head.name = 'RobotHead'
    
    # Create the left arm
    bpy.ops.mesh.primitive_cube_add(size=0.2, location=(-0.7, 0, 1.5))
    left_arm = bpy.context.object
    left_arm.scale[1] = 2.5
    left_arm.name = 'RobotLeftArm'
    
    # Create the right arm
    bpy.ops.mesh.primitive_cube_add(size=0.2, location=(0.7, 0, 1.5))
    right_arm = bpy.context.object
    right_arm.scale[1] = 2.5
    right_arm.name = 'RobotRightArm'
    
    # Create the left leg
    bpy.ops.mesh.primitive_cube_add(size=0.2, location=(-0.3, 0, 0.3))
    left_leg = bpy.context.object
    left_leg.scale[1] = 2.5
    left_leg.name = 'RobotLeftLeg'
    
    # Create the right leg
    bpy.ops.mesh.primitive_cube_add(size=0.2, location=(0.3, 0, 0.3))
    right_leg = bpy.context.object
    right_leg.scale[1] = 2.5
    right_leg.name = 'RobotRightLeg'

# Function to animate the robot running
def animate_robot():
    bpy.context.scene.frame_start = 1
    bpy.context.scene.frame_end = 40

    left_leg = bpy.data.objects['RobotLeftLeg']
    right_leg = bpy.data.objects['RobotRightLeg']
    left_arm = bpy.data.objects['RobotLeftArm']
    right_arm = bpy.data.objects['RobotRightArm']

    # Animation for left leg
    left_leg.rotation_euler[0] = 0.0
    left_leg.keyframe_insert(data_path="rotation_euler", frame=1)
    left_leg.rotation_euler[0] = 0.5
    left_leg.keyframe_insert(data_path="rotation_euler", frame=20)
    left_leg.rotation_euler[0] = 0.0
    left_leg.keyframe_insert(data_path="rotation_euler", frame=40)
    
    # Animation for right leg
    right_leg.rotation_euler[0] = 0.5
    right_leg.keyframe_insert(data_path="rotation_euler", frame=1)
    right_leg.rotation_euler[0] = 0.0
    right_leg.keyframe_insert(data_path="rotation_euler", frame=20)
    right_leg.rotation_euler[0] = 0.5
    right_leg.keyframe_insert(data_path="rotation_euler", frame=40)
    
    # Animation for left arm
    left_arm.rotation_euler[0] = 0.5
    left_arm.keyframe_insert(data_path="rotation_euler", frame=1)
    left_arm.rotation_euler[0] = 0.0
    left_arm.keyframe_insert(data_path="rotation_euler", frame=20)
    left_arm.rotation_euler[0] = 0.5
    left_arm.keyframe_insert(data_path="rotation_euler", frame=40)
    
    # Animation for right arm
    right_arm.rotation_euler[0] = 0.0
    right_arm.keyframe_insert(data_path="rotation_euler", frame=1)
    right_arm.rotation_euler[0] = 0.5
    right_arm.keyframe_insert(data_path="rotation_euler", frame=20)
    right_arm.rotation_euler[0] = 0.0
    right_arm.keyframe_insert(data_path="rotation_euler", frame=40)

# Clear any previous mesh objects
bpy.ops.object.select_all(action='DESELECT')
bpy.ops.object.select_by_type(type='MESH')
bpy.ops.object.delete()

# Create and animate the robot
create_robot()
animate_robot()


