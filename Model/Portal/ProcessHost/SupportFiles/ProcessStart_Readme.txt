    <!-- 
    This file is used to configure the execution of workflows based on data events.

    
    <event name="{EVENT TYPE}">
        <entityType name="{ENTITY TYPE}" memberFilter="{PROPERTY LIST}" condition="{CONDITION}">
            <runProcess name="{WORKFLOW NAME}" />
        </entityType>
    </event>
    <event ...>

	{EVENT TYPE} indicates the type of notification for which to run the configured workflows
		Created			=> Raise an event when a new entity is created
		Deleted			=> Raise an event when an existing entity is deleted
		PropertyChanged => Raise an event when an existing entity is updated, based on the subscribed properties in the memberFilter attribute

	{ENTITY TYPE} should be a fully qualified .NET type name indicating the entity to watch
	    1 or more <entityType> elements may be present.
	
	{PROPERTY LIST} is a comma separated list of properties on the {ENTITY TYPE} that are being watched for changes.
	    It is important to note that only properties mapped to database columns can be watched.  
		These entries are case sensitive.

	{WORKFLOW NAME} specifies the class name of the workflow to be executed.
	    1 or more <runProcess> elements may be present.
		The processLib.xml must be configured with the appropriate assembly which this workflow is contained within.

	
	{CONDITION} specifies a condition which must be met before the process is started.  The condition may be combined with other
	  conditions using an AND or OR conjunction.  Each condition must be enclosed in parentheses and a string value must be enclosed in
	  quotes.  Conditional entity properties do not need to be included in the memberFilter attribute.  A condition's value is case-sensitive.
	  For example, a memberFilter may be Status on the Opportunity entity and the condition could be 
	  "(Status = 'Closed-Won') AND (SalesPotential &gt;= 1000000)".
    -->

  <!-- sample

  <event name="PropertyChanged">
    <entityType name="Sage.Entity.Interfaces.IAccount, Sage.Entity.Interfaces" memberFilter="Division" condition="(Division='HQ')">
      <runProcess name="DivisionSendMail" />
    </entityType>
  </event>

-->