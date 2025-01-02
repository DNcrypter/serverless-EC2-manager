# Serverless EC2 Instance Scheduler for Company Working Hours 
## Scenario :
In some companies, there is no need to run their EC2 instances 24/7; they require instances to operate during specific time periods, such as company working hours, from 8:00 AM in the morning to 5:00 PM in the evening. To address this scenario, I will implement two Lambda functions responsible for starting and stopping instances. These Lambda functions will be triggered by two CloudWatch Events in the morning and evening. This solution is fully serverless.

![Blank diagram](https://github.com/DNcrypter/serverless-EC2-manager/images/block diagram.png)


## Steps :

### Step 1 :
### Creating the Instance :
1. Navigate to the EC2 Console.
2. Follow the Outlined steps below.

![a1](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a1.png)


![a2](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a2.png)


![a3](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a3.png)


![a4](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a4.png)


![a5](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a5.png)


![a6](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a6.png)


### Step 2 :
### Creating the Policy :


1. Navigate to the IAM Console.
2. Click on "Policies" and then Click on "Create policy"


![a7](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a7.png)


3. Select services as EC2.
4. And Actions are DescribeInstances , StartInstances.


![a8](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a8.png)


![a9](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a9.png)



![a10](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a10.png)


![a11](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a11.png)


![a12](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a12.png)


![a13](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a13.png)
5. Now we have created a policy for starting instances. We also need to create a policy for stopping the instances. This is because we are going to create two Lambda functions: one for starting and one for stopping the instances. Each function will have its own role, and we will attach these two policies to their respective roles.<br>
6. Now  we are going to repeat the same steps for Creating Stopping Policy also.<br>
7. Everything is same , Except Actions because we are going to stop the instance.<br>
8. The Actions are DescribeInstances , StopInstances .<br>
9. Keep your Plolicy name as "stop-ec2-instance".

## Step 3 :
## Creating the Lambda functions :

1. Navigate to the lambda Console.
2. Follow the Outlined steps below.


![a14](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a14.png)


![a15](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a15.png)


![a16](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a16.png)


![a17](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a17.png)

![Screenshot 2024-02-23 065451](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/s1.png)

![Screenshot 2024-02-23 065512](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/s2.png)

![a18](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a18.png)


![a19](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a19.png)


![a20](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a20.png)


![a21](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a21.png)


![a22](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a22.png)


![a23](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a23.png)


![a24](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a24.png)

Now again , go to the Lambda console and then test the code.
![a25](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a25.png)
![a26](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a26.png)


3. Now we Created  alambda function for Starting Instance.
4. We have to Reapeat the same steps again to Create a Lambda function for Stopping Instance , Keep your lambda function name as "Stop-EC2-demo".
5. The only changes we have to make are to replace the default code with the 'stop-ec2-instance.py' code and attach the policy we created for stopping instances to the role of this Lambda function.


![a27](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a27.png)

6. As demonstrated above, when I test my Python code, it runs successfully and stops the instance.
7. Now, we are ready to proceed and create schedules for this functions.

### Step 5 :
### Creating the Schedules Using Cloud Watch :

1. Navigate to the Cloud Watch Console.
2. Follow the Outlined Steps below.


![a28](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a28.png)



![a29](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a29.png)


![a30](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/a30.png)
#### Note : Keep your rule name as "start-ec2-rule" , I mistakenly named it 'role' Please do not name it as 'role.'





![b1](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b1.png)


![b1 1](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b1-1.png)


![b2](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b2.png)


![b3](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b3.png)


![b4](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b4.png)


![b5](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b5.png)


![b6](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b6.png)


![b7](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b7.png)


![b8](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b8.png)


3. We have now created a schedule for starting the instance every day at 8:00 AM.<br>
4. Next, we need to create a schedule for stopping instances.<br>
5. To create the schedule for stopping instances, follow the same steps as for starting instance scheduling with a few changes, Keep your rule name as "stop-ec2-rule".<br>
6. The changes include modifying the scheduled time and selecting the appropriate scheduling function.<br>
7. We need to change the schedule time to 17:00 because it will stop the Lambda function at 17:00 IST (5:00 PM).

![b9](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b9.png)

8. We have to Change the Function as Stop-EC2-demo

![b10](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b10.png)

9. Now, we have successfully created two schedules: one to start the instance every day at 8:00 AM and the other to stop the instance every day at 5:00 PM.


![b11](https://github.com/DNcrypter/serverless-EC2-manager/blob/main/images/b11.png)


