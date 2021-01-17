---
layout: default
title: ow.waf
parent: Reference
grand_parent: OpenAF docs
---


## ow.waf

### ow.waf.bpm.deleteSemaphore

__ow.waf.bpm.deleteSemaphore(aAF, aSemaphoreName) : Map__

````
For a given aAF WAF connection will delete the semaphore identified by aSemaphoreName.
````
### ow.waf.bpm.findFlowsByName

__ow.waf.bpm.findFlowsByName(aAF, flowName, listOfFlows, exactMatch) : Array__

````
Returns a list of flows, for the aAF server, which contain the flowName in the flow name. Optionally you can provide a listOfFlows as a result of ow.waf.bpm.listFlows to avoid an extra call to retrieve that list.
````
### ow.waf.bpm.getFlowCategories

__ow.waf.bpm.getFlowCategories(aAF) : Array__

````
Returns a list of flow categories for the aAF server provided.
````
### ow.waf.bpm.getFlowInstances

__ow.waf.bpm.getFlowInstances(aAF, aFlowStatus) : Array__

````
For the provided aAF server, tries to retrieve all instances/executions with a given aFlowStatus with the values:

   -1 - Flow stopped
    0 - Terminated
    1 - Created
    2 - Running
    3 - In error
    4 - Finished
    5 - Discarded
    6 - Suspended 

````
### ow.waf.bpm.getFlowInstancesByName

__ow.waf.bpm.getFlowInstancesByName(aAF, aFlowName, aFlowStatus) : Array__

````
For the provided aAF server, tries to retrieve the flow instances/executions with a given aFlowStatus with the values:

   -1 - Flow stopped
    0 - Terminated
    1 - Created
    2 - Running
    3 - In error
    4 - Finished
    5 - Discarded
    6 - Suspended 

````
### ow.waf.bpm.getSemaphores

__ow.waf.bpm.getSemaphores(aAF) : Array__

````
For a given aAF WAF connection retrieves a list of semaphores as an array.
````
### ow.waf.bpm.listFlows

__ow.waf.bpm.listFlows(aAF) : Array__

````
Returns an array with a list of flows for a given aAF server. Each element has flowName, flowTypeId (or category id), flowTypeDescription, engine and flowObjId (or flow id).
````
### ow.waf.bpm.loadFlow

__ow.waf.bpm.loadFlow(aAF, flowId) : JavaParameterMap__

````
Given an aAF server and a flowId will return the raw JavaParameterMap that includes the flow definition.
NOTE: the flow definition can't be retrieved through a liferay connection. Do connect directly to the
````
### ow.waf.bpm.runFlowById

__ow.waf.bpm.runFlowById(aAF, flowObjId, shouldWait, args) : Map__

````
Returns a the execution result, for the aAF server, from executing flowObjId. Optionally you can provide if shouldWait  (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map.
````
### ow.waf.bpm.runFlowByNameAndVersion

__ow.waf.bpm.runFlowByNameAndVersion(aAF, flowName, flowVersion, shouldWait, args) : Map__

````
Returns the execution results, for the aAF server, of executing flowName with flowVersion. Optionally you can provide if shouldWait (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map.
````
### ow.waf.bpm.runFlowsByName

__ow.waf.bpm.runFlowsByName(aAF, flowName, shouldWait, args, listOfFlows) : Array__

````
Returns a list of flows execution results (each flow will have a results entry), for the aAF server,  where flow names which contain the flowName will be executed. Optionally you can provide if shouldWait  (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map. You can provide also a listOfFlows as a result of ow.waf.bpm.listFlows to avoid an extra  call to retrieve that list.
````
### ow.waf.bpm.saveFlow

__ow.waf.bpm.saveFlow(aAF, rawJavaPMFlowDefinition, aCachedFlowList) : Map__

````
Tries to lock, validate, modify and save, in the aAF server, the flow definition provided in  a Java parameter  map rawJavaPMFlowDefinition. Throws an error if any operation fails. If successful will return the result of the save  flow definition operation. Optionally you can provide a listOfFlows as a result of ow.waf.bpm.listFlows to avoid an extra call to retrieve that list.
````
### ow.waf.bpm.saveSemaphore

__ow.waf.bpm.saveSemaphore(aAF, aSemaphoreDef) : Map__

````
For a given aAF WAF connection will add or modify (if the semaphore name already exists) aSemaphoreDef (usually obtain from the elements of ow.waf.im.getSemaphores). If a new semaphore is created the new semaphore def will be returned.
````
### ow.waf.bpm.setModifyOnProdFlows

__ow.waf.bpm.setModifyOnProdFlows(aAF, aModifyFlag)__

````
Modifies the flow life cycle flag that determines if a production flow version can be changed (aModifyFlag = true) or if any change will require a new version.
````
### ow.waf.bpm.unlockFlowsByName

__ow.waf.bpm.unlockFlowsByName(aAF, flowName, isForce, listOfFlows) : Array__

````
Returns a list of results, for the aAF server, of trying to unlock flows whose names contain the flowName.  Optionally you can provide a listOfFlows as a result of ow.waf.bpm.listFlows to avoid an extra call to  retrieve that list. If isForce = true the session locking a flow will be killed.
````
### ow.waf.bpmn.findFlowsByName

__ow.waf.bpmn.findFlowsByName(aAF, flowName, listOfFlows, exactMatch) : Array__

````
Returns a list of BPMN flows, for the aAF server, which contain the flowName in the flow name. Optionally you can provide a listOfFlows as a result of ow.waf.cbpm.listFlows to avoid an extra call to retrieve that list.
````
### ow.waf.bpmn.getFlowInstances

__ow.waf.bpmn.getFlowInstances(aAF, flowUUID, anArrayOfStatus, limitRecords, sortByEndTime, sortAsc) : Array__

````
For a given aAF server, try to retrieve the BPMN flow instances for a flowUUID. Optionally you can specify one or more status in anArrayOfStatus (e.g 'FINISHED', 'ERROR', ...). Also, if necessary, it's possible to limitRecords for performance reasons given that the result is always sorted descending by startTime except if sortByEndTime = true and/or sortAsc = true.
````
### ow.waf.bpmn.getFlowInstancesByName

__ow.waf.bpmn.getFlowInstancesByName(aAF, flowName, anArrayOfStatus, limitRecords, sortByEndTime, sortAsc) : Array__

````
For a given aAF server, try to retrieve the BPMN flow instances for a flowName. Optionally you can specify one or more status in anArrayOfStatus (e.g 'FINISHED', 'ERROR', ...). Also, if necessary, it's possible to limitRecords for performance reasons given that the result is always sorted descending by startTime except if sortByEndTime = true and/or sortAsc = true.
````
### ow.waf.bpmn.listFlows

__ow.waf.bpmn.listFlows(aAF) : Array__

````
Returns an array with a list of BPMN flows for a given aAF server. Each element has flowName, flowTypeId (or category id), flowTypeDescription, engine and flowObjId (or flow id).
````
### ow.waf.bpmn.runFlowByName

__ow.waf.bpmn.runFlowByName(aAF, flowName, shouldWait, args, listOfFlows, exactMatch) : Map__

````
Returns the execution results, for the aAF server, of executing flowName. Optionally you can provide if shouldWait (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map. An exception will be thrown if more than one flow is found for flowName. Use runFlowByUUID alternatively.
````
### ow.waf.bpmn.runFlowByUUID

__ow.waf.bpmn.runFlowByUUID(aAF, flowUUID, shouldWait, args) : Map__

````
Returns the execution results, for the aAF server, of executing flowUUID. Optionally you can provide if shouldWait (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map.
````
### ow.waf.bulk

__ow.waf.bulk(aAF) : BulkObject__

````
Enables executing af operations, on the aAF server, in bulk. Returns a BulkObject with the methods exec(aOperation, aMapIn, aOperationName):BulkObject which adds aOperation with aMapIn referenced optionally by aOperationName to be executed in buik and get() that executes the current list of operations in bulk and returns a map with results (an entry per each execution with aOperationName containing result and error and a boolean resultErrors. Example:

va res = ow.waf.bulk(af)
         .exec("aOperation1", { x: 1, y: 2 }, "Op1")
         .exec("aOperation2". { x: 3, y: 4 }, "Op2")
         .get()
\
````
### ow.waf.cbpm.deleteSemaphore

__ow.waf.cbpm.deleteSemaphore(aAF, aSemaphoreName) : Map__

````
For a given aAF WAF connection will delete the semaphore identified by aSemaphoreName.
````
### ow.waf.cbpm.findFlowsByName

__ow.waf.cbpm.findFlowsByName(aAF, flowName, listOfFlows, exactMatch) : Array__

````
Returns a list of CBPM flows, for the aAF server, which contain the flowName in the flow name. Optionally you can provide a listOfFlows as a result of ow.waf.cbpm.listFlows to avoid an extra call to retrieve that list.
````
### ow.waf.cbpm.getFlowInstances

__ow.waf.cbpm.getFlowInstances(aAF, flowUUID, anArrayOfStatus, limitRecords, sortByEndTime, sortAsc) : Array__

````
For a given aAF server, try to retrieve the CBPM flow instances for a flowUUID. Optionally you can specify one or more status in anArrayOfStatus (e.g 'FINISHED', 'ERROR', ...). Also, if necessary, it's possible to limitRecords for performance reasons given that the result is always sorted descending by startTime except if sortByEndTime = true and/or sortAsc = true.
````
### ow.waf.cbpm.getFlowInstancesByName

__ow.waf.cbpm.getFlowInstancesByName(aAF, flowName, anArrayOfStatus, limitRecords, sortByEndTime, sortAsc) : Array__

````
For a given aAF server, try to retrieve the CBPM flow instances for a flowName. Optionally you can specify one or more status in anArrayOfStatus (e.g 'FINISHED', 'ERROR', ...). Also, if necessary, it's possible to limitRecords for performance reasons given that the result is always sorted descending by startTime except if sortByEndTime = true and/or sortAsc = true.
````
### ow.waf.cbpm.getSemaphores

__ow.waf.cbpm.getSemaphores(aAF) : Array__

````
For a given aAF WAF connection retrieves a list of semaphores as an array.
````
### ow.waf.cbpm.listFlows

__ow.waf.cbpm.listFlows(aAF) : Array__

````
Returns an array with a list of CBPM flows for a given aAF server. Each element has flowName, flowTypeId (or category id), flowTypeDescription, engine and flowObjId (or flow id).
````
### ow.waf.cbpm.runFlowByName

__ow.waf.cbpm.runFlowByName(aAF, flowName, shouldWait, args, listOfFlows, exactMatch) : Map__

````
Returns the execution results, for the aAF server, of executing flowName. Optionally you can provide if shouldWait (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map. An exception will be thrown if more than one flow is found for flowName. Use runFlowByUUID alternatively.
````
### ow.waf.cbpm.runFlowByUUID

__ow.waf.cbpm.runFlowByUUID(aAF, flowUUID, shouldWait, args) : Map__

````
Returns the execution results, for the aAF server, of executing flowUUID. Optionally you can provide if shouldWait (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map.
````
### ow.waf.cbpm.saveSemaphore

__ow.waf.cbpm.saveSemaphore(aAF, aSemaphoreDef) : Map__

````
For a given aAF WAF connection will add or modify (if the semaphore name already exists) aSemaphoreDef (usually obtain from the elements of ow.waf.cbpm.getSemaphores). If a new semaphore is created the new semaphore def will be returned.
````
### ow.waf.cbpm.unlockFlowsByName

__ow.waf.cbpm.unlockFlowsByName(aAF, flowName, isForce, listOfFlows) : Array__

````
Returns a list of results, for the aAF server, of trying to unlock flows whose names contain the flowName.  Optionally you can provide a listOfFlows as a result of ow.waf.cbpm.listFlows to avoid an extra call to  retrieve that list. If isForce = true the session locking a flow will be killed.
````
### ow.waf.datamodel.buildQuery

__ow.waf.datamodel.buildQuery(anArrayOfFields, anArrayOfFilters, anArrayOfOrders, mapOptions, mapBindValues) : Map__

````
Returns a map with a datamodel query provided with anArrayOfFields, anArrayOfFilters, anArrayOfOrders, a mapOptions and a mapBindValues. To build the mapOptions you can use ow.waf.datamodel.buildQueryOptions. See an example on ow.waf.datamodel.getQueryId.
````
### ow.waf.datamodel.buildQueryOptions

__ow.waf.datamodel.buildQueryOptions(isAllRows, isDistinct, aDomain, extra) : Map__

````
Builds and returns a datamodel query options providing if the query will be performed isAllRows (or first rows otherwise) and if isDistinct or not. Optionally you can merge extra arguments.
Version: WAF >= 7.0.x
````
### ow.waf.datamodel.cancelQueryId

__ow.waf.datamodel.cancelQueryId(aAF, aQueryId)__

````
Tries to cancel aQueryId (from ow.waf.datamodel.getQueryId) for the aAF server.
Version: WAF >= 7.0.x
````
### ow.waf.datamodel.closeQueryId

__ow.waf.datamodel.closeQueryId(aAF, aQueryId)__

````
Closes the provided aQueryId (from ow.waf.datamodel.getQueryId) for the aAF server.
Version: WAF >= 7.0.x
````
### ow.waf.datamodel.getAllContexts

__ow.waf.datamodel.getAllContexts(aAF, withMeta) : Array__

````
Returns an array with all the datamodel contexts. Optionally you can specify if you need also complete metadata per each.
````
### ow.waf.datamodel.getFoldersTree

__ow.waf.datamodel.getFoldersTree(aAF, aRootFolder, cachedListOfFolders) : String__

````
Given aAF server connection will try to build a string representation of the datamodel folder hierarchy (usually helpfull to use with moveLogicalFieldsFolder). Optionally you can provide aRootFolder UUID (defaults to the DM.Root folder object) and a previously cachedListOfFolders (obtained using ow.waf.datamodel.getAllFolders).
````
### ow.waf.datamodel.getQueryId

__ow.waf.datamodel.getQueryId(aAF, aQuery) : Map__

````
Tries to prepare a datamodel query, on the aAF server, returning a query id map, provided aQuery with anArrayOfFields, anArrayOfFilters, anArrayOfOrders, a mapOptions and a mapBindValues. To build the mapOptions you can use ow.waf.datamodel.buildQueryOptions. Example:

var qId = ow.waf.datamodel.getQueryId(server, 
  ow.waf.datamodel.buildQuery(
    ["Round(Sum({Total Charges}), 2) as 'Score'", "{Call Date}"],
    ["({Call Date} >= :startDate AND {Call Date} < :endDate)"],
    ["{Call Date} desc"],
    ow.waf.datamodel.buildQueryOptions(),
    { "startDate" : wedoDate("2014", "06", "04", "00", "00", "00", "000"),
      "endDate"   : wedoDate("2014", "06", "05", "00", "00", "00", "000") }
  )
);

print(beautifier(ow.waf.datamodel.getSQLFromId(server, qId)));
ow.waf.datamodel.closeQueryId(qId);

Version: WAF >= 7.0.x
````
### ow.waf.datamodel.getQueryInfoFromQueryId

__ow.waf.datamodel.getQueryInfoFromQueryId(aAF, aQueryId) : Map__

````
Returns a map with internal datamodel query information for the provided aQueryId on the aAF server.
Version: WAF >= 7.1.x.
````
### ow.waf.datamodel.getRowsFromQueryId

__ow.waf.datamodel.getRowsFromQueryId(aAF, aQueryId, aFirstRow, aNumRows) : Map__

````
Returns a results map from performing the datamodel aQueryId. If aFirstRow is not provided, row 1 will be assumed. If aNumRow is not provided, 100 rows will be assumed. Use aFirstRow and aNumRows to retrieve more data from the  datamodel query. The return results map will have a Status, the LastRowSelected and the a Data array.
Version: WAF >= 7.0.x
````
### ow.waf.datamodel.getSQLFromQueryId

__ow.waf.datamodel.getSQLFromQueryId(aAF, aQueryId) : Map__

````
Returns a SQL query plan (or just a generic query plan for none SQL data sources) for the aAF server given aQueryId provide by ow.waf.datamodel.getQueryId.
Version: WAF >= 7.0.x
````
### ow.waf.datamodel.moveLogicalFieldsFolder

__ow.waf.datamodel.moveLogicalFieldsFolder(aAF, aLFREName, aTargetFolder, aSourceFolder)__

````
Given aAF server connection will try to identify a list of logical fields whose name matches the regular expression aLFREName (optionally if aSourceFolder is provided they must be associated with the aSourceFolder UUID). All the identified logical fields will be added to the aTargetFolder UUID. If aSourceFolder is provided the logical fields will also be removed from the source folder.
````
### ow.waf.dp.generateValue

__ow.waf.dp.generateValue(aAF, aName, aStrategy) : Map__

````
For the given aAF server, generates a new value using the key generation aName. Optionally you can specify the aStrategy, if not it will default to "Numeric Sequence".
````
### ow.waf.dp.getKeyGen

__ow.waf.dp.getKeyGen(aAF, aName, aStrategy) : Map__

````
For the given aAF server, retrieves all info regarding key generation aName. Optionally you can specify the aStrategy, if not it will default to "Numeric Sequence".
````
### ow.waf.dp.getKeyGenDef

__ow.waf.dp.getKeyGenDef(aName, extra) : Map__

````
Prepares a key generation definition map for aName. Optionally you can override options with a extra map. Example:

ow.waf.dp.saveKeyGen(af, ow.waf.dp.getKeyGenDef("test", { 
   Entry: {
      MaxValue: 10,
      InitialValue: 0,
      Increment: 2
   }
}));


````
### ow.waf.dp.getKeyGens

__ow.waf.dp.getKeyGens(aAF, aStrategy): Array__

````
For the given aAF server, retrieves an array of available key generation (e.g. sequences) entries. If a specific aStrategy is not provided, all available strategies will be considered.
````
### ow.waf.dp.getKeyGenStrategies

__ow.waf.dp.getKeyGenStrategies(aAF) : Array__

````
For the given aAF server, retrieves the current DataPump Key Generation strategies available in an array of maps.
````
### ow.waf.dp.getLoadingProcesses

__ow.waf.dp.getLoadingProcesses(aAF) : Array__

````
Returns an array of the current datapump loading processes for the given aAF WAF connection. The array is composed of name, specId, objId, specUUID, objUUID and version number.
````
### ow.waf.dp.getLookup

__ow.waf.dp.getLookup(aAF, aLookupName) : Map__

````
For a given aAF WAF connection will try to find the exact lookup with the name aLookupName. If aLookupName is a number it wil be use as the table id to retrieve the lookup. Once found the current definition and configuration (under the map key config) will be retrieved.
````
### ow.waf.dp.getLPStatusReport

__ow.waf.dp.getLPStatusReport(aAF, loadingProcessId, limitMap, includeInputParams, alternativeAdmDB, errorFunc) : Array__

````
For the given aAF server and the provided datapump loadingProcessId will retrive each run status report (using the Adm database access). Optionally you can provide an alternativeAdmDB object. You can also indicate, with includeInputParams = true, that input parameters should be included. An errorFunc receiving a message and an exception and a limitMap can optionally be added. The limitMap can include: startDate (string of date), endDate (string of date), objId, status (number), and rows (limit number of rows).
````
### ow.waf.dp.listLookups

__ow.waf.dp.listLookups(aAF) : Array__

````
For a given aAF WAF connection will retrieve a list, in the form of an array, of available datapump lookup names.
````
### ow.waf.dp.removeKeyGen

__ow.waf.dp.removeKeyGen(aAF, aName, aStrategy) : Map__

````
For the given aAF server, tries to remove an existing key generation aName. Optionally you can specify the aStrategy, if not it will default to "Numeric Sequence".
````
### ow.waf.dp.requestUnload

__ow.waf.dp.requestUnload(aAF, aLookupName, aList)__

````
For a given aAF WAF connection will try to find the exact lookup with the name aLookupName. Once found a unload request will be submitted. You can check when the request is processed using  ow.waf.datapump.getLookup. You can also optionally provide an already cached list of lookups aList (using ow.waf.dp.listLookups).
````
### ow.waf.dp.resetKeyGen

__ow.waf.dp.resetKeyGen(aAF, aName, aValue, aStrategy, extra) : Map__

````
For a given aAF server, tries to reset a key generation aName with the aValue (defaults to 1). Optionally you can provide aStrategy (defaults to "Numeric Sequence") and override any options with an extra map.
````
### ow.waf.dp.saveKeyGen

__ow.waf.dp.saveKeyGen(aAF, aKeyGenDef) : Map__

````
For the given aAF server, tries to create a non existing or add a new version for a key generation defined by aKeyGenDef. Example:

ow.waf.dp.saveKeyGen(af, ow.waf.dp.getKeyGenDef("test", { Entry: { MaxValue: 10 } });


````
### ow.waf.gc

__ow.waf.gc(aAF) : Map__

````
Tries to trigger a garbage collector operation on the aAF server.
````
### ow.waf.getAFCredentialsFromProductConfig

__ow.waf.getAFCredentialsFromProductConfig(aFile) : Map__

````
Given a product-config.xml aFile will try to return a map with user, pass and port useing the ServerAdmin* and ServerPort entries.
````
### ow.waf.getAFFromInstanceProductConfig

__ow.waf.getAFFromInstanceProductConfig(aFile) : AF__

````
Given a product-config.xml aFile will try to return an instatiated AF object for the ServerAdminUser.
````
### ow.waf.getAFServerVersion

__ow.waf.getAFServerVersion(aAF) : String__

````
Given aAF (an AF object instance) will perform a GetServerVersion AF operation an return the reported version (for the AF server).
````
### ow.waf.getInstancePrivileges

__ow.waf.getInstancePrivileges(aAF, flat, fullPriv) : Object__

````
Given aAF (an AF object instance) will return an object with all visibility and owner of permissions for each object type (same info as in the Portal's Instance Security). If flat = true the output will be a flat array of privilege entries otherwise it will be a map divided by object types. If fullPriv = true the output will be a flat array of privilege entries with each  object corresponding permissions object retrived and added in the Privileges array on each entry. You can use ow.waf.objects.setPrivileges( aAF, result.SpecUUID, result.Permissions) to change any entry.
````
### ow.waf.getInstances

__ow.waf.getInstances(aAF) : Array__

````
Given aAF (an AF object instance) will return a list with the current instance and other connected instances.
````
### ow.waf.getMajorVersion

__ow.waf.getMajorVersion(aAF) : Number__

````
Given aAF (an AF object instance) will try to guess the major WAF version of the server. The result will be a number representing the major version (e.g. 63 = 6.3.x; 70 = 7.0.x; etc...)
````
### ow.waf.getMemoryInfo

__ow.waf.getMemoryInfo(aAF, convertNumbers) : Map__

````
Returns the AF server memory usage. If convertNumbers = true it will convert the results to float numbers and add a date field.
````
### ow.waf.getServerConnections

__ow.waf.getServerConnections(aAF) : Array__

````
Given aAF (an AF object instance) will return a list with the current instance connection and other connected instances.
````
### ow.waf.getSessions

__ow.waf.getSessions(aAF) : Map__

````
Returns the AF server current sessions statistics and details.
````
### ow.waf.getSystemProperties

__ow.waf.getSystemProperties(aAF) : Map__

````
Returns the AF server Java system properties. (available after ow.loadWAF())
````
### ow.waf.getThreadDump

__ow.waf.getThreadDump(aAF, isRaw) : Array__

````
Tries to return the current aAF server thread dump. If isRaw = true it won't convert the StackFrame component to an array.
````
### ow.waf.getVersion

__ow.waf.getVersion(aAf) : String__

````
Given aAf (an AF object instance) will perform a GetServerVersion AF operation to the server and then  try to guess, using an internal mapping, to which RAID version corresponds the server. The internal mapping starts on versions 6.3.x up to the latest GA version available. The return value will be either the specific version (e.g. "7.1.2") or at least the major version if the specific is not found (e.g. "7.1"). Otherwise the return value will be "" (see also getVersion)
````
### ow.waf.housekeeping.cleanAudit

__ow.waf.housekeeping.cleanAudit(aAF, minAgeDays) : Map__

````
Cleans object auditing older than minAgeDays from the aAF server. Optionally you can provide an executionId.
````
### ow.waf.housekeeping.cleanDeletedObjects

__ow.waf.housekeeping.cleanDeletedObjects(aAF minAgeDays, executionId) : Map__

````
Cleans from the database objects marked as deleted older than minAgeDays from the aAF server.  Optionally you can provide an executionId.
````
### ow.waf.housekeeping.cleanObjectsVersions

__ow.waf.housekeeping.cleanObjectsVersions(aAF, minAgeDays, versionsToKeep, executionId) : Map__

````
Cleans object versions older that minAgeDays will trying to keep a minimum versionsToKeep (defaults to 1) from the aAF server. Optionally you can provide an executionId.
````
### ow.waf.housekeeping.markDeleteObjects

__ow.waf.housekeeping.markDeleteObjects(aAF, minAgeDays, executionId) : Map__

````
Marks objects older that minAgeDays as deleted from the aAF server. Optionally you can provide an executionId.
````
### ow.waf.im.deleteFileFormat

__ow.waf.im.deleteFileFormat(aAF, aId) : Map__

````
For a given aAF WAF connection will delete the file format identified by aId.
````
### ow.waf.im.deleteImport

__ow.waf.im.deleteImport(aAF, aTaskId) : Map__

````
For a given aAF WAF connection will delete the import task identified by aTaskId.
````
### ow.waf.im.deleteLookup

__ow.waf.im.deleteLookup(aAF, aId) : Map__

````
For a given aAF WAF connection will delete the lookup identified by aId.
````
### ow.waf.im.getLookup

__ow.waf.im.getLookup(aAF, aLookupName) : Map__

````
For a given aAF WAF connection will try to find the exact lookup with the name aLookupName. If aLookupName is a number it wil be use as the table id to retrieve the lookup. Once found the current definition and configuration (under the map key config) will be retrieved.
````
### ow.waf.im.listFileFormats

__ow.waf.im.listFileFormats(aAF) : Array__

````
For a given aAF WAF connection will return the list of existing IM file formats.
````
### ow.waf.im.listImports

__ow.waf.im.listImports(aAF) : Array__

````
For a given aAF WAF connection will retrieve a list, in the form of an array, of available import tasks.
````
### ow.waf.im.listLookups

__ow.waf.im.listLookups(aAF) : Array__

````
For a given aAF WAF connection will retrieve a list, in the form of an array, of available lookup names.
````
### ow.waf.im.reorderImport

__ow.waf.im.reorderImport(aAF, taskId, afterTaskId)__

````
For a given aAF WAF connection changes the order of the import task taskId to be after afterTaskId.
````
### ow.waf.im.requestUnload

__ow.waf.im.requestUnload(aAF, aLookupName)__

````
For a given aAF WAF connection will try to find the exact lookup with the name aLookupName. Once found a unload request will be submitted. You can check when the request is processed using  ow.waf.im.getLookup.
````
### ow.waf.im.saveFileFormat

__ow.waf.im.saveFileFormat(aAF, aFileFormatDef) : Map__

````
For a given aAF WAF connection will add or modify (if the file format id already exists) aFileFormatDef (usually obtain from the elements of ow.waf.im.listFileFormats). If a new FileFormat is created the new FileFormat Id will be returned.
````
### ow.waf.im.saveImport

__ow.waf.im.saveImport(aAF, anImportDef) : Map__

````
For a given aAF WAF connection will add or modify (if the import id already exists) anImportDef (usually obtain from the elements of ow.waf.im.listImports). If a new import task is created the new task id will be returned.
````
### ow.waf.im.saveLookup

__ow.waf.im.saveLookup(aAF, aLookupDef) : Map__

````
For a given aAF WAF connection will add or modify (if the lookup id already exists) aLookupDef (usually obtain from the elements of ow.waf.im.getLookup). If a new lookup is created the new lookup Id will be returned.
````
### ow.waf.im.useLookup

__ow.waf.im.useLookup(aAF, aLookupName, anArrayOfValues) : Map__

````
For a given aAF WAF connection will try to find the exact lookup with the name aLookupName. Then the anArrayOfValues will be used to retrieve values from that lookup. The result will be a Map with a boolean Matched and a Results map. If the lookup is not found an exception will  be thrown.
````
### ow.waf.internalCurrentThread

__ow.waf.internalCurrentThread() : JavaThreadSession__

````
Returns the current internal thread to be used with internalExec and internalExecRaw.
````
### ow.waf.internalExec

__ow.waf.internalExec(aOperation, pmIn, aThread) : Object__

````
When using inside RAID (OpenAF4RAID) will execute an AF operation using the current session.

Example from a bean shell task:

_out[0].setParameters(openaf.OpenAF.exec(_in, "__pmOut.oo = ow.loadWAF().internalExec('GetServerVersion', __pmIn);")); _setOut.setExit(0);


````
### ow.waf.internalExecRaw

__ow.waf.internalExecRaw(aOperation, javaParameterMapIn, aThread) : JavaParameterMap__

````
When using inside RAID (OpenAF4RAID) will execute an AF operation using the current session. All input and output  parameter maps are Java ParameterMaps.
````
### ow.waf.mashups.getMashupByName

__ow.waf.mashups.getMashupByName(aAF, aLookupName, ignoreCase, loadTags) : Map__

````
Given aLookupName will return the first mashup (if any), on the aAF server, where shortname or description is partially matchs aLookupName ignoring case (if ignoreCase = true). Optionally loading tags (loadTags = true).
Version: WAF >= 7.1.x
````
### ow.waf.mashups.getMashupByUUID

__ow.waf.mashups.getMashupByUUID(aAF, aSpecUUID, loadTags) : Map__

````
Given aSpecUUID will return the corresponding mashup definition, from aAF server, optionally loading tags (loadTags = true)
Version: WAF >= 7.1.x
````
### ow.waf.mashups.getMashupsByName

__ow.waf.mashups.getMashupsByName(aAF, aLookupName, ignoreCase) : Array__

````
Given aLookupName will return an array of mashups metadata (including UUID), on the aAF server, where shortname or description is partially matchs aLookupName ignoring case (if ignoreCase = true)
Version: WAF >= 7.1.x
````
### ow.waf.mashups.saveMashup

__ow.waf.mashups.saveMashup(aAF, objDefinition, ignoreSession, saveAsNew) : Map__

````
Tries to save the mashup objDefinition (as provided by ow.waf.mashups.getMashup*) for a given aAF server. Optionally you can specify to lock the mashup ignoring locks by others sessions using ignoreSession = true. If saveAsNew = true then the objDefinition will be used to create a new mashup (change the shortname if you don't want it to equal the mashup title).
Version: WAF >= 7.0.x
````
### ow.waf.objects.addPrivileges

__ow.waf.objects.addPrivileges(privDefintion, aSubject, aTarget, canAssignPrivs, canDelete, canEdit, canView) : Map__

````
Will return a new privileges definition where for a specific aSubject (name of user, role or usergroup), whose type is defined by aTarget (e.g. owner, role, user, usergroup), specifing if canAssignPrivs, canDelete, canEdit and/or canView. 
Version: WAF >= 7.0.x
````
### ow.waf.objects.addPublicViewPrivileges

__ow.waf.objects.addPublicViewPrivileges(privDefinition) : Map__

````
Will return a new privileges definition with public privileges to all users.
Version: WAF >= 7.0.x
````
### ow.waf.objects.deleteObjects

__ow.waf.objects.deleteObjects(aAF, aListOfUUIDs, deleteCascade) : Map__

````
Tries to delete the objects provided on the aListOfUUIDs array. Additionally you can provide a deleteCascade boolean parameter.
````
### ow.waf.objects.getAllObjects

__ow.waf.objects.getAllObjects(aAF, withObjDef, withTags, withAllVersions) : Map__

````
Returns an array of all objects, for a given aAF server. Optionally you can specify if you want the object definition to be retrieved (slow, use getObjectByUUID to retrieve the definition) withObjDef = true, the object  tags withTags = true and all object versions withAllVersions.
````
### ow.waf.objects.getAllVersionsByUUID

__ow.waf.objects.getAllVersionsByUUID(aAF, aSpecUUID) : Array__

````
Tries to retrieve, from the aAF server, all versions (objUUIDs) of the provided aSpecUUID. USe ow.waf.objects.getVersionByUUID with  the returned objUUIDs. Version: WAF >= 8.0.9
````
### ow.waf.objects.getChildObjectsByName

__ow.waf.objects.getChildObjectsByName(aAF, aLookupName, ignoreCase, objType) : Map__

````
Given aLookupName will return the child objects (on a "childs" array) for the first object (if any), on the aAF server,  where shortname or description is partially matchs aLookupName ignoring case (if ignoreCase = true). Optionally you can specify the objType to narrow the selection.
Version: WAF >= 7.1.x
````
### ow.waf.objects.getChildObjectsByUUID

__ow.waf.objects.getChildObjectsByUUID(aAF, aSpecUUID) : Map__

````
Given aSpecUUID will return the corresponding child objects, from aAF server. The child objects will be  returned as an array "childs" on the returned map. Version: WAF >= 7.1.x
````
### ow.waf.objects.getObjectByName

__ow.waf.objects.getObjectByName(aAF, aLookupName, ignoreCase, loadTags, objType) : Map__

````
Given aLookupName will return the first object (if any), on the aAF server, where shortname or description is partially matchs aLookupName ignoring case (if ignoreCase = true). Optionally loading tags (loadTags = true). Optionally you can specify the objType to narrow the selection.
Version: WAF >= 7.1.x
````
### ow.waf.objects.getObjectByUUID

__ow.waf.objects.getObjectByUUID(aAF, aSpecUUID, loadTags) : Map__

````
Given aSpecUUID will return the corresponding object definition, from aAF server, optionally loading tags (loadTags = true).
Version: WAF >= 7.1.x
````
### ow.waf.objects.getObjectsByName

__ow.waf.objects.getObjectsByName(aAF, aLookupName, ignoreCase, objType) : Array__

````
Given aLookupName will return an array of objects metadata (including UUID), on the aAF server, where shortname or description is partially matchs aLookupName ignoring case (if ignoreCase = true). Optionally you can specify the objType to narrow the selection.
Version: WAF >= 7.1.x
````
### ow.waf.objects.getObjectsByType

__ow.waf.objects.getObjectsByType(aAF, aLookupType) : Array__

````
Given aLookupType will return an array of objects metadata (including UUID), on the aAF server, where the object type  corresponds.
Version: WAF >= 7.1.x
````
### ow.waf.objects.getObjectTypes

__ow.waf.objects.getObjectTypes(aAF, secure) : Array__

````
Returns an array of object types, for a given aAF server. Optionally you can specify if you want secure = true.
Version: WAF >= 7.0.x
````
### ow.waf.objects.getParentObjectsByName

__ow.waf.objects.getParentObjectsByName(aAF, aLookupName, ignoreCase, objType) : Array__

````
Returns an array of parent objects for the given aLookupName (will return the first object (if any), on the aAF server, where shortname or description is partially matchs aLookupName ignoring case (if ignoreCase = true)). Optionally you can specify the objType to narrow the selection.
Version: WAF >= 8.x
````
### ow.waf.objects.getParentObjectsByUUID

__ow.waf.objects.getParentObjectsByUUID(aAF, aSpecUUID) : Array__

````
Returns an array of parent objects for aSpecUUID on the aAF server. Version: WAF >= 8.x
````
### ow.waf.objects.getPrivileges

__ow.waf.objects.getPrivileges(aAF, aObjUUID) : Map__

````
Get the privileges for a specific aObjUUID from the aAF server.
Version: WAF >= 7.0.x
````
### ow.waf.objects.getVersionByUUID

__ow.waf.objects.getVersionByUUID(aAF, aSpecUUID, aObjUUID) : Map__

````
Get the object definition, from the aAF server, given the corresponding aObjUUID for aSpecUUID (tip: objUUIDs can be retrieved using ow.waf.objects.getAllVersionsByUUID). Version: WAF >= 7.1.x
````
### ow.waf.objects.lockObject

__ow.waf.objects.lockObject(aAF, aSpecUUID, ignoreSession) : Map__

````
Tries to lock the aSpecUUID on the aAF server. Optionally ignore other session locks (ignoreSession = true). Will return a Map with the current version information.
Version: WAF >= 7.0.x
````
### ow.waf.objects.saveObject

__ow.waf.objects.saveObject(aAF, aObject, extraOptions) : Map__

````
Tries to save the aObject on the aAF server. Please do keep in mind that you should use higher level operations to ensure proper validation of the object being saved is performed. You can add extraOptions (depending on version) like:
   replaceExistingParents (boolean)
   createNewVersion (boolean)
   keepLock (boolean)
   relations (map with key "add" or "delete" with an array with parentUUID, childUUID and qualification)
   objectPrivs (map with privileges and "replaceExisting" (boolean) or "inheritParentPermissions" (boolean) or "newOwnerName" (string))
   saveOnLatestVersion (boolean)
   newUUID (that will be considered if specUUID is ommited)
\  Version: WAF >= 7.0.x
````
### ow.waf.objects.saveObjectWithNoVersion

__ow.waf.objects.saveObjectWithNoVersion(aAF, aObject, extraOptions) : Map__

````
Similar to ow.waf.objects.saveObjectWithNoVersion but adding, as extra options, the option saveOnLatestVersion = true and createNewVersion = false.
````
### ow.waf.objects.saveObjectWithSpecUUID

__ow.waf.objects.saveObjectWithSpecUUID(aAF, aSpecUUID, aObject, extraOptions) : Map__

````
Checks if an object with aSpecUUID exists and if it doesn't ensures that the specUUID will be aSpecUUID using the ow.waf.objects.saveObject using aAF, aObject and extraOptions. Note: if aSpecUUID is deleted an error will be thrown.
````
### ow.waf.objects.setPrivileges

__ow.waf.objects.setPrivileges(aAF, aObjUUID, privDefinition, inheritParentPermissions, newOwnerName)__

````
Tries to set the privileges provided by privDefinition for a specific aObjUUID, from the aAF server. Optionally  you can specify that parent privileges should be inherit. If newOwnerName is defined it will try to change the owner.
Version: WAF >= 7.0.x
````
### ow.waf.objects.unlockObject

__ow.waf.objects.unlockObject(aAF, aSpecUUID, ignoreSession) : Map__

````
Tries to unlock the aSpecUUID on the aAF server. Optionally ignore other session locks (ignoreSession = true). Will return a Map with the current version information.
Version: WAF >= 7.0.x
````
### ow.waf.objects.unsetPrivileges

__ow.waf.objects.unsetPrivileges(aAF, aObjUUID, privDefinition, inheritParentPermissions)__

````
Tries to unset the privileges provided by privDefinition for a specific aObjUUID, from the aAF server.
Version: WAF >= 7.0.x
````
### ow.waf.operationsTraceCommand

__ow.waf.operationsTraceCommand(aAF, anEntry, simulateOutput, fullException) : String__

````
Given a aAF server connection and an operations trace anEntry returns the corresponding unix commands to create a file for input, if necessary, and execute the operation with the corresponding input. Optionally if simulateOutput is true a simulation of the af-run-cmd output will be included. If fullException is also true a stack trace simulation will also  be included. Note: for a more accurate simulation you should use a non RAID portal connection.
````
### ow.waf.operationsTraceCommandsReplay

__ow.waf.operationsTraceCommandsReplay(aAF, aCh, simulateOutput, fullException) : String__

````
For the provided aAF server connection and aCh channel with operations trace will execute ow.waf.operationsTraceCommand for each entry (with the optionals simulateOutput and fullException), concatenate the output and return it.
````
### ow.waf.ping

__ow.waf.ping(aAF, someEcho) : Map__

````
Returns the result of sending a someEcho Map to aAF server (should be equal for version >= 7.0) (available after ow.loadWAF())
````
### ow.waf.scheduler.checkJobsRunning

__ow.waf.scheduler.checkJobsRunning(aAF, jobUUIDEntriesArray) : Map__

````
Returns information, for an aAF server, is a scheduler job, for each jobUUIDEntriesArray, is currently active for running or not.
````
### ow.waf.scheduler.getJobEntries

__ow.waf.scheduler.getJobEntries(aAF) : Array__

````
For a given aAF WAF connection (version >= 8) will return the list of scheduler entries.
````
### ow.waf.scheduler.getJobEntryExecutions

__ow.waf.scheduler.getJobEntryExecutions(aAF, jobUUIDEntry, lastModified, recordsPerPage, page, op) : Array__

````
Returns an array with all the scheduler jobUUIDEntry executions. Optionally you can specify lastModified boolean to be different from false, recordsPerPage number to be different from the 27 default and page number to be different from 1 default.
````
### ow.waf.scheduler.retryJob

__ow.waf.scheduler.retryJob(aAF, jobEntryUUID) : Map__

````
Tries, for an aAF server, to retry an "on-demand" job execution for jobEntryUUID.
````
### ow.waf.scheduler.startJobEntries

__ow.waf.scheduler.startJobEntries(aAF, jobUUIDEntriesArray) : Map__

````
For a given aAF WAF connection (version >= 8) and anArrayOfEntries UUID (jobEntryUUID) values will try top start (activate) the corresponding scheduler entries.
````
### ow.waf.scheduler.stopJobEntries

__ow.waf.scheduler.stopJobEntries(aAF, anArrayOfEntries) : Map__

````
For a given aAF WAF connection (version >= 8) and anArrayOfEntries UUID (jobEntryUUID) values will try top stop (inactivate) the corresponding scheduler entries.
````
### ow.waf.setOpenAFLanguage

__ow.waf.setOpenAFLanguage(aAF, aOpenAFJarPath)__

````
Adds or replaces an object on the aAF object instance to declare OpenAF as a scripting language in RAID. Optionally a aOpenAFJarPath can be used to force the path to OpenAF.
````
### ow.waf.startOperationsTrace

__ow.waf.startOperationsTrace(aAF, aCh)__

````
Starts tracing af operations, on the provided aAF connection, a storing trace data into the aCh channel. If aCh is ommited a channel "OpenCli::operationsTrace" will be created.
````
### ow.waf.stopOperationsTrace

__ow.waf.stopOperationsTrace(aAF)__

````
Stops tracing af operations, on the provided aAF connection.
````
### ow.waf.unsetOpenAFLanguage

__ow.waf.unsetOpenAFLanguage(aAF, aOpenAFJarPath)__

````
Deletes an object on the aAF object instance to declare OpenAF as a scripting language in RAID.
````
### ow.wafc.bpmn.runFlowsByName

__ow.wafc.bpmn.runFlowsByName(aAF, flowName, shouldWait, args, listOfFlows) : Array__

````
Returns a list of flows execution results (each flow will have a results entry), for the aAF server,  where flow names which contain the flowName will be executed. Optionally you can provide if shouldWait  (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map. You can provide also a listOfFlows as a result of ow.waf.bpmn.listFlows to avoid an extra  call to retrieve that list.
````
### ow.wafc.cbpm.runFlowsByName

__ow.wafc.cbpm.runFlowsByName(aAF, flowName, shouldWait, args, listOfFlows) : Array__

````
Returns a list of flows execution results (each flow will have a results entry), for the aAF server,  where flow names which contain the flowName will be executed. Optionally you can provide if shouldWait  (boolean) for the end of the execution of flows and a args map containing entry map, entry_name and/or share map. You can provide also a listOfFlows as a result of ow.waf.cbpm.listFlows to avoid an extra  call to retrieve that list.
````
