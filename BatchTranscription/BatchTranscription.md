<h1>Batch Transcription</h1>
<h2>Private Endpoint Consideration</h2>
Batch Transcription consists of Speech Services and Storage Services such like Azure Storage Account.
<br>The operational flow of batch transcription is,</br>
<br><ul>
  <li>Place audio files on to the storage services</li>
  <li>Set the url or SAS to the batch transcription REST call or SDK script, and run it</li>
  <li>Retrieve the transcript file</li>
</ul></br>

<img src="..\images\batchTranscription1.png" width="70%">

<br>
As can be seen in the diagram above, even REST call or SDK script command being issued inside a private network, data flow takes place outside of it.
<br>SAS should be strong enough to prevent malicious attach from peeking the data. However, the enterprise customer might not be satisfied with it. Eventually need stronger mechanism in place.</br>
<br>In such a situation, consider and configure using System-assigned Managed ID access from Speech Service.

Refer to [Bring your own storage (BYOS) for customization and logging](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-encryption-of-data-at-rest#bring-your-own-storage-byos-for-customization-and-logging)
<br>
<h3>STEP1</h3>
Configure BYOS when deploying the speech services
<img src="..\images\storage0.png" width="70%">

</br><br>
<h3>STEP2</h3>
Configure Storage Account Settings at Configuration blade
<br>Disable "Blob Public Access"</br>
<img src="..\images\storage1.png" width="70%">

<br>Set "Resource Type" and "Instance Name" at Networking blade</br>
<img src="..\images\storage2.png" width="70%">

<br>Verify "Storage Blob Data Contributor" at Access Control blade</br>
<img src="..\images\storage3.png" width="70%">

<h3>STEP3</h3>
Issue create transcription
<br>
Input url doesn't need sas when the audio file is placed on the storage configured with the settings above. 
<br>
"destinationContainerUrl" is not necessary, either.
</br>
The transcription data is placed at "TranscriptionData" folder in "customspeech-artifacts" container of the storage.
</br><br><i>Sample REST call</i>

```json

{
  "contentUrls": [
    "https://<storageFqdn>/<containerName>/audioFile.wav"
  ],
  "properties": {
    "diarizationEnabled": false,
    "wordLevelTimestampsEnabled": false,
    "punctuationMode": "DictatedAndAutomatic",
    "profanityFilterMode": "None",
    "timeToLive": "PT12H"
  },
  "locale": "ja-JP",
  "displayName": "Transcription using default model for ja-JP"
}

```