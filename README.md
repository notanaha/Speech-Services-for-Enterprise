<h1>Speech Services for Enterprise</h1>
<h2>What is enterprise requirements?</h2>
For enterprise customers, the following functionality need available.
<i><ul>
  <li>Access Control</li>
  <li>Network Security</li>
  <li>Data Isolation</li>
  <li>Audit</li>
</ul></i>

As Speech Services consists of several services, need to prioritize documentation.

<i><ul>
  <li>Batch transcription</li>
  <li>Realtime transcription</li>
  <li>Conversation transcription</li>
  <li>Text to speech</li>
  <li>Speech translation</li>
  <li>Speaker Recognition</li>
  and so on...
</ul></i>

We start documentation from <i>Batch Transcription</i> as it includes several resources to function.
<br><br>

<h1>Batch transcription</h1>
Batch Transcription gets access to Blob Storage when Create transcription was issued. For that network traffic, Batch Transcription needs extra concern to configure Network Security and Data Isolation.
<br><br>

<h2>Network Security</h2>
<h3>Private Network Access</h3>
<br>
Cognitive Services provides an option to configure private network access. 

[Configure Azure Cognitive Services virtual networks](https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-virtual-networks?tabs=portal)
<br>


For Speech Services, you may have limitation for making use of Speech Studio. Take a careful look at the following articles.
<br>

[Use Speech service through a private endpoint](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-services-private-link?tabs=portal)
<br>
- When private endpoint is configured, the networking page shows the entry of the private endpoint.
<br>
<img src=".\images\privep1.png" width="70%">

[Use Speech service through a Virtual Network service endpoint](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-service-vnet-service-endpoint)
<br>
- When service endpoint is configured, the networking page shows the selected network.
<br>
<img src=".\images\servep1.png" width="70%">

<br>
<h2>Data Isolation</h2>
<h3>Bring Your Own Storage</h3>
<br>

It is stated that Speech Service automatically encrypts the data when it is persisted it to the cloud.<br>
[Speech service encryption of data at rest](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-encryption-of-data-at-rest)
<br>

For Batch Transcription, [Bring Your Own Storage](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-encryption-of-data-at-rest#bring-your-own-storage-byos-for-customization-and-logging) more makes sense in a way that BYOS makes it possible to isolate data in your own subscription.
<br>

As to how to configure BOYS for Batch Transcription, refer to the following page.
<br>

[Configure BYOS for Batch Transcription](./BatchTranscription/BatchTranscription.md) 
<br><br>
<img src=".\images\batchTranscription1.png" width="70%">
<br><br>

<h2>Access Control</h2>
<h3>Authentication</h3>
<br>

Speech Service can provide Authentication via API key as always is the case with Cognitive Services. 
Follow [Find keys and location/region](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/overview#try-the-speech-service-for-free) section to find API Key.<br>
For the other options for Authentication, refer to [Authenticate requests to Azure Cognitive Services](https://docs.microsoft.com/en-us/azure/cognitive-services/authentication)
<br><br>

<h2>Audit</h2>
<h3>diagnostic logging</h3>
<br>
It is possible for Cognitive Services to enable diagnostic logging.
<br>

The topic is explained in [Enable diagnostic logging for Azure Cognitive Services](https://docs.microsoft.com/en-us/azure/cognitive-services/diagnostic-logging)

As to the other aspect of Audit related topics, take a look at the following documents.
<br>

[Azure Policy built-in policy definitions for Azure Cognitive Services](https://docs.microsoft.com/en-us/azure/cognitive-services/policy-reference)
<br>

[Azure security baseline for Cognitive Services](https://docs.microsoft.com/en-us/security/benchmark/azure/baselines/cognitive-services-security-baseline)