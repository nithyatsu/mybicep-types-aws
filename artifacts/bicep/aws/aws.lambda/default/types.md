# AWS.Lambda @ default

## Resource AWS.Lambda/CodeSigningConfig@default
* **Valid Scope(s)**: Unknown
### Properties
* **alias**: string (Required): the resource alias
* **name**: string: the resource name
* **properties**: [AWS.Lambda/CodeSigningConfigProperties](#awslambdacodesigningconfigproperties) (Required): properties of the resource

## Resource AWS.Lambda/EventSourceMapping@default
* **Valid Scope(s)**: Unknown
### Properties
* **alias**: string (Required): the resource alias
* **name**: string: the resource name
* **properties**: [AWS.Lambda/EventSourceMappingProperties](#awslambdaeventsourcemappingproperties) (Required): properties of the resource

## Resource AWS.Lambda/Function@default
* **Valid Scope(s)**: Unknown
### Properties
* **alias**: string (Required): the resource alias
* **name**: string: the resource name
* **properties**: [AWS.Lambda/FunctionProperties](#awslambdafunctionproperties) (Required): properties of the resource

## Resource AWS.Lambda/Url@default
* **Valid Scope(s)**: Unknown
### Properties
* **alias**: string (Required): the resource alias
* **name**: string: the resource name
* **properties**: [AWS.Lambda/UrlProperties](#awslambdaurlproperties) (Required): properties of the resource

## AWS.Lambda/CodeSigningConfigProperties
### Properties
* **AllowedPublishers**: [AllowedPublishers](#allowedpublishers) (Required): When the CodeSigningConfig is later on attached to a function, the function code will be expected to be signed by profiles from this list
* **CodeSigningConfigArn**: string (ReadOnly, Identifier): A unique Arn for CodeSigningConfig resource
* **CodeSigningConfigId**: string (ReadOnly): A unique identifier for CodeSigningConfig resource
* **CodeSigningPolicies**: [CodeSigningPolicies](#codesigningpolicies): Policies to control how to act if a signature is invalid
* **Description**: string: A description of the CodeSigningConfig

## AllowedPublishers
### Properties
* **SigningProfileVersionArns**: string[] (Required): List of Signing profile version Arns

## CodeSigningPolicies
### Properties
* **UntrustedArtifactOnDeployment**: string (Required): Indicates how Lambda operations involve updating the code artifact will operate. Default to Warn if not provided

## AWS.Lambda/EventSourceMappingProperties
### Properties
* **AmazonManagedKafkaEventSourceConfig**: [AmazonManagedKafkaEventSourceConfig](#amazonmanagedkafkaeventsourceconfig): Specific configuration settings for an MSK event source.
* **BatchSize**: int: The maximum number of items to retrieve in a single batch.
* **BisectBatchOnFunctionError**: bool: (Streams) If the function returns an error, split the batch in two and retry.
* **DestinationConfig**: [DestinationConfig](#destinationconfig): (Streams) An Amazon SQS queue or Amazon SNS topic destination for discarded records.
* **DocumentDBEventSourceConfig**: [DocumentDBEventSourceConfig](#documentdbeventsourceconfig): Document db event source config.
* **Enabled**: bool: Disables the event source mapping to pause polling and invocation.
* **EventSourceArn**: string: The Amazon Resource Name (ARN) of the event source.
* **FilterCriteria**: [FilterCriteria](#filtercriteria): The filter criteria to control event filtering.
* **FunctionName**: string (Required): The name of the Lambda function.
* **FunctionResponseTypes**: string[]: (Streams) A list of response types supported by the function.
* **Id**: string (ReadOnly, Identifier): Event Source Mapping Identifier UUID.
* **MaximumBatchingWindowInSeconds**: int: (Streams) The maximum amount of time to gather records before invoking the function, in seconds.
* **MaximumRecordAgeInSeconds**: int: (Streams) The maximum age of a record that Lambda sends to a function for processing.
* **MaximumRetryAttempts**: int: (Streams) The maximum number of times to retry when the function returns an error.
* **ParallelizationFactor**: int: (Streams) The number of batches to process from each shard concurrently.
* **Queues**: string[]: (ActiveMQ) A list of ActiveMQ queues.
* **ScalingConfig**: [ScalingConfig](#scalingconfig): The scaling configuration for the event source.
* **SelfManagedEventSource**: [SelfManagedEventSource](#selfmanagedeventsource): Self-managed event source endpoints.
* **SelfManagedKafkaEventSourceConfig**: [SelfManagedKafkaEventSourceConfig](#selfmanagedkafkaeventsourceconfig): Specific configuration settings for a Self-Managed Apache Kafka event source.
* **SourceAccessConfigurations**: [SourceAccessConfiguration](#sourceaccessconfiguration)[]: A list of SourceAccessConfiguration.
* **StartingPosition**: string: The position in a stream from which to start reading. Required for Amazon Kinesis and Amazon DynamoDB Streams sources.
* **StartingPositionTimestamp**: int: With StartingPosition set to AT_TIMESTAMP, the time from which to start reading, in Unix time seconds.
* **Topics**: string[]: (Kafka) A list of Kafka topics.
* **TumblingWindowInSeconds**: int: (Streams) Tumbling window (non-overlapping time window) duration to perform aggregations.

## AmazonManagedKafkaEventSourceConfig
### Properties
* **ConsumerGroupId**: string: The identifier for the Kafka Consumer Group to join.

## DestinationConfig
### Properties
* **OnFailure**: [OnFailure](#onfailure): The destination configuration for failed invocations.

## OnFailure
### Properties
* **Destination**: string: The Amazon Resource Name (ARN) of the destination resource.

## DocumentDBEventSourceConfig
### Properties
* **CollectionName**: string: The collection name to connect to.
* **DatabaseName**: string: The database name to connect to.
* **FullDocument**: string: Include full document in change stream response. The default option will only send the changes made to documents to Lambda. If you want the complete document sent to Lambda, set this to UpdateLookup.

## FilterCriteria
### Properties
* **Filters**: [Filter](#filter)[]: List of filters of this FilterCriteria

## Filter
### Properties
* **Pattern**: string: The filter pattern that defines which events should be passed for invocations.

## ScalingConfig
### Properties
* **MaximumConcurrency**: int: The maximum number of concurrent functions that the event source can invoke.

## SelfManagedEventSource
### Properties
* **Endpoints**: [Endpoints](#endpoints): The endpoints for a self-managed event source.

## Endpoints
### Properties
* **KafkaBootstrapServers**: string[]: A list of Kafka server endpoints.

## SelfManagedKafkaEventSourceConfig
### Properties
* **ConsumerGroupId**: string: The identifier for the Kafka Consumer Group to join.

## SourceAccessConfiguration
### Properties
* **Type**: string: The type of source access configuration.
* **URI**: string: The URI for the source access configuration resource.

## AWS.Lambda/FunctionProperties
### Properties
* **Architectures**: string[]
* **Arn**: string (ReadOnly): Unique identifier for function resources
* **Code**: [Code](#code) (Required, WriteOnly): The code for the function.
* **CodeSigningConfigArn**: string: A unique Arn for CodeSigningConfig resource
* **DeadLetterConfig**: [DeadLetterConfig](#deadletterconfig): A dead letter queue configuration that specifies the queue or topic where Lambda sends asynchronous events when they fail processing.
* **Description**: string: A description of the function.
* **Environment**: [Environment](#environment): Environment variables that are accessible from function code during execution.
* **EphemeralStorage**: [EphemeralStorage](#ephemeralstorage): A function's ephemeral storage settings.
* **FileSystemConfigs**: [FileSystemConfig](#filesystemconfig)[]: Connection settings for an Amazon EFS file system. To connect a function to a file system, a mount target must be available in every Availability Zone that your function connects to. If your template contains an AWS::EFS::MountTarget resource, you must also specify a DependsOn attribute to ensure that the mount target is created or updated before the function.
* **FunctionName**: string (Identifier): The name of the Lambda function, up to 64 characters in length. If you don't specify a name, AWS CloudFormation generates one.
* **Handler**: string: The name of the method within your code that Lambda calls to execute your function. The format includes the file name. It can also include namespaces and other qualifiers, depending on the runtime
* **ImageConfig**: [ImageConfig](#imageconfig): ImageConfig
* **KmsKeyArn**: string: The ARN of the AWS Key Management Service (AWS KMS) key that's used to encrypt your function's environment variables. If it's not provided, AWS Lambda uses a default service key.
* **Layers**: string[]: A list of function layers to add to the function's execution environment. Specify each layer by its ARN, including the version.
* **MemorySize**: int: The amount of memory that your function has access to. Increasing the function's memory also increases its CPU allocation. The default value is 128 MB. The value must be a multiple of 64 MB.
* **PackageType**: string: PackageType.
* **ReservedConcurrentExecutions**: int: The number of simultaneous executions to reserve for the function.
* **Role**: string (Required): The Amazon Resource Name (ARN) of the function's execution role.
* **Runtime**: string: The identifier of the function's runtime.
* **RuntimeManagementConfig**: [RuntimeManagementConfig](#runtimemanagementconfig): RuntimeManagementConfig
* **SnapStart**: [SnapStart](#snapstart): The SnapStart setting of your function
* **SnapStartResponse**: [SnapStartResponse](#snapstartresponse) (ReadOnly): The SnapStart response of your function
* **Tags**: [Tag](#tag)[]: A list of tags to apply to the function.
* **Timeout**: int: The amount of time that Lambda allows a function to run before stopping it. The default is 3 seconds. The maximum allowed value is 900 seconds.
* **TracingConfig**: [TracingConfig](#tracingconfig): Set Mode to Active to sample and trace a subset of incoming requests with AWS X-Ray.
* **VpcConfig**: [VpcConfig](#vpcconfig): For network connectivity to AWS resources in a VPC, specify a list of security groups and subnets in the VPC.

## Code
### Properties
* **ImageUri**: string (WriteOnly): ImageUri.
* **S3Bucket**: string (WriteOnly): An Amazon S3 bucket in the same AWS Region as your function. The bucket can be in a different AWS account.
* **S3Key**: string (WriteOnly): The Amazon S3 key of the deployment package.
* **S3ObjectVersion**: string (WriteOnly): For versioned objects, the version of the deployment package object to use.
* **ZipFile**: string (WriteOnly): The source code of your Lambda function. If you include your function source inline with this parameter, AWS CloudFormation places it in a file named index and zips it to create a deployment package..

## DeadLetterConfig
### Properties
* **TargetArn**: string: The Amazon Resource Name (ARN) of an Amazon SQS queue or Amazon SNS topic.

## Environment
### Properties
* **Variables**: [Function_Variables](#functionvariables): Environment variable key-value pairs.

## Function_Variables
### Properties

## EphemeralStorage
### Properties
* **Size**: int (Required): The amount of ephemeral storage that your function has access to.

## FileSystemConfig
### Properties
* **Arn**: string (Required): The Amazon Resource Name (ARN) of the Amazon EFS access point that provides access to the file system.
* **LocalMountPath**: string (Required): The path where the function can access the file system, starting with /mnt/.

## ImageConfig
### Properties
* **Command**: string[]: Command.
* **EntryPoint**: string[]: EntryPoint.
* **WorkingDirectory**: string: WorkingDirectory.

## RuntimeManagementConfig
### Properties
* **RuntimeVersionArn**: string: Unique identifier for a runtime version arn
* **UpdateRuntimeOn**: string (Required): Trigger for runtime update

## SnapStart
### Properties
* **ApplyOn**: string (Required): Applying SnapStart setting on function resource type.

## SnapStartResponse
### Properties
* **ApplyOn**: string (ReadOnly): Applying SnapStart setting on function resource type.
* **OptimizationStatus**: string (ReadOnly): Indicates whether SnapStart is activated for the specified function version.

## Tag
### Properties
* **Key**: string (Required): The key name of the tag. You can specify a value that is 1 to 128 Unicode characters in length and cannot be prefixed with aws:. You can use any of the following characters: the set of Unicode letters, digits, whitespace, _, ., /, =, +, and -.
* **Value**: string: The value for the tag. You can specify a value that is 0 to 256 Unicode characters in length and cannot be prefixed with aws:. You can use any of the following characters: the set of Unicode letters, digits, whitespace, _, ., /, =, +, and -.

## TracingConfig
### Properties
* **Mode**: string: The tracing mode.

## VpcConfig
### Properties
* **SecurityGroupIds**: string[]: A list of VPC security groups IDs.
* **SubnetIds**: string[]: A list of VPC subnet IDs.

## AWS.Lambda/UrlProperties
### Properties
* **AuthType**: string (Required): Can be either AWS_IAM if the requests are authorized via IAM, or NONE if no authorization is configured on the Function URL.
* **Cors**: [Cors](#cors)
* **FunctionArn**: string (ReadOnly, Identifier): The full Amazon Resource Name (ARN) of the function associated with the Function URL.
* **FunctionUrl**: string (ReadOnly): The generated url for this resource.
* **InvokeMode**: string: The invocation mode for the function?s URL. Set to BUFFERED if you want to buffer responses before returning them to the client. Set to RESPONSE_STREAM if you want to stream responses, allowing faster time to first byte and larger response payload sizes. If not set, defaults to BUFFERED.
* **Qualifier**: string (WriteOnly): The alias qualifier for the target function. If TargetFunctionArn is unqualified then Qualifier must be passed.
* **TargetFunctionArn**: string (Required, WriteOnly): The Amazon Resource Name (ARN) of the function associated with the Function URL.

## Cors
### Properties
* **AllowCredentials**: bool: Specifies whether credentials are included in the CORS request.
* **AllowHeaders**: string[]: Represents a collection of allowed headers.
* **AllowMethods**: string[]: Represents a collection of allowed HTTP methods.
* **AllowOrigins**: string[]: Represents a collection of allowed origins.
* **ExposeHeaders**: string[]: Represents a collection of exposed headers.
* **MaxAge**: int

