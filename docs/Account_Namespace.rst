Namespace
=======================================================

A Namespace is a collection of Data Streams.

	For HTTP requests and responses, the Namespace object has the following properties and JSON-serialized body: 

.. _NamespaceObj: 

``String Id``
	Name of this Namespace. Unique within a Tenant's Namespaces.
``String TenantId``
	GUID of the Tenant that this Namespace corresponds to
``String Description``
	Description of this Namespace.
``String TierId``
	GUID of the Tier that this Namespace is associated with.
``Int32 ThroughputUnits``
	Number of Throughput units for this Namespace.
``Int32 StorageUnits``
	Number of Storage units for this Namespace.
``NamespaceProvisioningState State``
	Current state of this Namespace.
``OwnerTrustee Owner``
	Represents a :ref:`Trustee <TrusteeObj>` that can be an owner of an :ref:`ISecurable <ISecurableObj>`.
``AccessControlList AccessControlList``
	Access Control List.

.. highlight:: C#

::

	HTTP/1.1 200
	Content-Type: application/json

 {
	"Id": "id",
	"TenantId": "tenantid",
	"Description": "description",
	"TierId": "tierid",
	"ThroughputUnits": 0,
	"StorageUnits": 0,
	"State": 0,
	"Owner":  {
		"Type": 2,
		"TenantId": "string",
		"ApplicationId": "string"
	 },
	"AccessControlList":  {
		"RoleTrusteeAccessControlEntries": []
	 }
 }

``GetAll()``
--------------------------------------------------------------------

Returns all :ref:`Namespace <NamespaceObj>`s owned by the specified tenant that the caller has access to.

**Http**

::

	GET api/Tenants/{tenantId}/Namespaces

**Parameters**

``String tenantId``
	The :ref:`Tenant <TenantObj>` identifier for the request.

**Security**
	:ref:`Read <ReadObj>` on governing :ref:`AccessControlList <AccessControlListObj>`.

**Returns**
	An array of all :ref:`Namespace <NamespaceObj>` objects for the specified tenantId that the caller has access.



|

**********************

``GetNamespaceById()``
--------------------------------------------------------------------

Returns the Namespace with the specified Id.

**Http**

::

	GET api/Tenants/{tenantId}/Namespaces/{namespaceId}

**Parameters**

``String tenantId``
	The account identifier for the request
``String namespaceId``
	The Namespace identifier for this request

**Security**
	Allowed by Account Member :ref:`Role <RoleObj>`

**Returns**
	A :ref:`Namespace <NamespaceObj>` object with the specified namespaceId



|

**********************

``Create()``
--------------------------------------------------------------------

Creates a namespace.

**Http**

::

	POST api/Tenants/{tenantId}/Namespaces

**Parameters**

``String tenantId``
	The idenfifier for the account the namespace is to be created for.
``Namespace namespaceObj``
	The :ref:`Namespace <NamespaceObj>` to be created.

**Security**
	Allowed by Account Member :ref:`Role <RoleObj>`

**Returns**
	The created :ref:`Namespace <NamespaceObj>` object



|

**********************

``Update()``
--------------------------------------------------------------------

Updates namespace information - description, tier Id, and AccessControl. Cannot specify Owner for a request.

**Http**

::

	PUT api/Tenants/{tenantId}/Namespaces/{namespaceId}

**Parameters**

``String tenantId``
	The identifier of namespace's account.
``String namespaceId``
	The identifier for the namespace to update.
``Namespace newProperties``
	The new details to store for the namespace.

**Security**
	Allowed by Account Member :ref:`Role <RoleObj>`

**Returns**
	The updated :ref:`Namespace <NamespaceObj>`.



|

**********************

``Delete()``
--------------------------------------------------------------------

Deletes a namespace.

**Http**

::

	DELETE api/Tenants/{tenantId}/Namespaces/{namespaceId}

**Parameters**

``String tenantId``
	The identifier of namespace's account
``String namespaceId``
	The identifier of the namespace to be deleted

**Security**
	Allowed by Account Member :ref:`Role <RoleObj>`

**Returns**
	Nothing is returned



|

**********************


