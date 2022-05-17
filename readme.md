WS IOT CAMERA SYSTEM
The project is about aws iot camera system,  the cameras will be sending streams to aws and aws will do **NVR** things and send the stream to the user.

#### IN SMASH.SH

#### CREATING A THING TYPE

To create a thing type enter the following commands ```"aws iot create-thing-type"``` and we give it the flag of the name of the thing type we creating and we store it in the **iot thing type**  file in json format.

#### CREATING A THING

A thing is a representation of specific device.
To create a thing we can use this command ```"aws iot create-thing"``` and we give it the flag of the thing name we are creating and the flag of the name of the thing type we created and we are writing to the **iot-thing.json** file.

### CREATING A ROLE

A role is a unique identity that has been assigned specific permissions which have been defined in a role policy file.

- To create a role you can use the following command ```"aws iam create-role"```.
- We do a flag ```role-name```to define a name.
    role-name is the name of the role being created, it has to be unique are not distinguished by case
- We attach a role policy by giving the flag ```assume-role-policy-document``` we give a path to the file role policy file.
- We write the **iam role.json** file.

### CREATING IAM ROLE POLICY

We are attaching the policy to the role using the following command ```aws iam put-role-policy```.

- To associate a **role policy name** and **iam  role name** we give a flag of the role name ```--role-name```.
- We give the flag of the policy name ```--policy-name```.
- Then the policy document is the one defining the permission or role for each user on the system. Then we give the flag ```--policy-document``` and we give path to the permission-document.

#### CREATE-ROLE-ALIAS

- We create role alias to have access to Amazon Resource Name (ARN).
- We create a role alias using the command ```aws iot create-role-alias```.
- We give flag of ```--role-alias```
- Then we give a flag of ```role-arn``` so that we can have access to the resources.
- we give the flag of ```credentials-duration-seconds 3600```. How long (in seconds) the credentials will be valid. The default value is 3,600 seconds, then the value must be less than or equal to the maximum session duration of the IAM role that the roles alias references.

### CAT>

We are creating a file name ```iot-policy-document.json``` and we are defining the **JSON policy document structure** .

- **Version** - Specifies the version of the policy language that you want to use such as 2012-10-17.
- **Statement** - Use this main policy element as a container for the following elements i.e
  - **Effect** – Use Allow or Deny to indicate whether the policy allows or denies access.
  - **Action** – Include a list of actions that the policy allows or denies.
  - **Resource** - Required in only some circumstances– In this case we have listed the resource in which actions apply ```iot-role-alias.json```.

### CREATE IOT-POLICY

  We are creating a iot-policy with the command ```aws iot create-policy```.
  - We give the flag of the policy name ```--policy-name```. 
  - Then the policy document is the one defining the permission to the iot-policy. Then we give the flag ```--policy-document``` and we give path to the permission-document.

### CREATING KEY AND CERTFICATE

  We are craeting the keys and certifcate with the command ```aws iot create-keys-and-certificate```.
  - We give the flag of ```--set-as-active``` , here we are setting our keys and certificate to be active.
  - **--certificate-pem-outfile** here we are creating the file to store our certificate in the pem format and give a path to the **certificate.pem**
  - **--public-key-outfile** we are creating the file to store our keys in the pem format and give a path to the **public.pem.key**.
  - **--private-key-outfile** we are creating the file to store our keys in the pem format and give a path to the **private.pem.key** 
  - Then we write the file **certificate**

  ### ATTACHING A POLICY TO A CERTIFICATE
  - We are attaching the policy to the certificate using the command ```aws iot attach-policy```.
  - Then the flag of the policy name which we are attaching to a certificate is ```--policy-name```.
  - We specify the certificate we are targeting ```--target``` and give the path where the certificate is located. 

  ### ATTACHING A PRINCIPAL TO A CERTIFICATE
  - We are attaching the principal to the certificate using the command ```aws iot attach-thing-principal ```.
  - Then the flag of the thing name which we are attaching to a certificate to ```--thing-name```
  - We give a flag of the principal ```--principal``` and path of the target certificate.