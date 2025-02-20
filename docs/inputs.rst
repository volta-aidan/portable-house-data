Portable House Data Inputs
==========================

The portable house data input file (json format) is designed to be flexible, allowing buildings to be defined at a variety of levels of detail. 
Where parameters are not required, recommended defaults are provided. 
However, it falls on the individual software provider or data interpreter to handle defaults within their own systems appropriately.

The file format contains two levels of nesting: *Category* and *Object Class*. *Categories* include: Building Information, Building Site, Enclosure, Systems, and Occupant Characteristics.

The **Required** field in the table below indicates whether a parameter is required in the context of that object class, but not all Object Classes are required. 
For example, if the ``foundation`` object class is included, the ``foundationType`` variable is also required. 
Object classes that are required indicate so in their section headers below.


Building Information
--------------------

Building Specifications (REQUIRED)
**********************************

The Building Specifications section is always required, meaning that the ``yearBuilt`` and ``totalConditionedFloorArea`` of the home are always required parameters

  ==================================  ========  =======  ===========  ========  ===========  ============================================================
  Variable Name                       Type      Units    Constraints  Required  Default      Notes
  ==================================  ========  =======  ===========  ========  ===========  ============================================================
  ``yearBuilt``                       integer                         Yes                    Year built of dwelling unit
  ``planShape``                       string             See [#]_     No        rectangular  Shape of home. Includes number of corners, aligned with ERS
  ``buildingType``                    string             See [#]_     No        detached     Type of dwelling
  ``facingDirection``                 string             See [#]_     No        S            Front-facing direction of building
  ``numConditionedFloors``            integer            > 0, <=4     No        1            Total number of storeys, including basement if applicable
  ``numConditionedFloorsAboveGrade``  integer            >= 0, <=3    No        1            Total number of above grade storeys
  ``layoutType``                      string             See [#]_     No        standard     Layout of storeys, used to indicate presence of split levels
  ``totalConditionedFloorArea``       double    m2       >0, <=600    Yes                    Total conditioned floor area of the building
  ==================================  ========  =======  ===========  ========  ===========  ============================================================

  .. [#] ``layoutType`` choices are "standard" and "split".
  .. [#] ``planShape`` choices are "rectangular", "t-shape", "l-shape", "5-6 corners", "7-8 corners", "9-10 corners", and "11 or more corners"
  .. [#] ``buildingType`` choices are "detached", "attached", "row-middle", "row-end", "murb unit", and "murb building"
  .. [#] ``facingDirection`` choices are "N", "NE", "E", "SE", "S", "SW", "W", and "NW"



Building Site
-------------
Location (REQUIRED)
***********************

Location information can be entered in four different ways depending on the level of detail provided.
These sections can be used in combination with eachother, but at least one of the following sets of data is required.

Address
~~~~~~~
  
  ==================================  ========  =======  ===========  ========  ===========  =============================================================
  Variable Name                       Type      Units    Constraints  Required  Default      Notes
  ==================================  ========  =======  ===========  ========  ===========  =============================================================
  ``address``                         string                          No                     Combination of the below three options (e.g. 123 Fake Street)
  ``addressCivicNumber``              string                          No                     Address number (e.g. 123, 2A)
  ``addressStreetName``               string                          No                     Address street name (e.g. Fake Street)
  ``addressUnitNumber``               string                          No                     Unit number, if applicable
  ==================================  ========  =======  ===========  ========  ===========  =============================================================

Postal Code
~~~~~~~~~~~
The postal code input allows either a full postal code (6 characters or 7 with a space), or the forward sortation area (FSA, first three digits of the postal code). 
  
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  Variable Name                       Type      Units    Constraints    Required  Default      Notes
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  ``postalCode``                      string             >=3, <7 char.  No                     Building's postal code or FSA
  ==================================  ========  =======  =============  ========  ===========  ============================================================

Region
~~~~~~~~~~~
  
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  Variable Name                       Type      Units    Constraints    Required  Default      Notes
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  ``city``                            string                            No                     City, town, or village name
  ``region``                          string             See [#]_       No                     Province, Territory, or State
  ``country``                         string                            No        CANADA       Country
  ==================================  ========  =======  =============  ========  ===========  ============================================================

  .. [#] ``region`` should use two-letter province/territory/state abbreviation ("ON", "QC", "YT", etc.)

Latitude & Longitude
~~~~~~~~~~~~~~~~~~~~
  
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  Variable Name                       Type      Units    Constraints    Required  Default      Notes
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  ``latitude``                        double    WGS84                   No                     Latitude of building
  ``longitude``                       double    WGS84                   No                     Longitude of building
  ==================================  ========  =======  =============  ========  ===========  ============================================================


Enclosure
---------

Air Infiltration
***********************

  ==================================  ========  =======  =============  ========  ===========  ============================================================
  Variable Name                       Type      Units    Constraints    Required  Default      Notes
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  ``airLeakageRate``                  double    ACH50                   No        See [#]_     Air leakage of dwelling
  ==================================  ========  =======  =============  ========  ===========  ============================================================

  .. [#] ``airLeakageRate`` defaults are not provided, assuming interpreters have a means of assuming defaults where measured values are not provided (e.g. ERS Technical Procedures Appendix D).



Foundation
***********************

  ==================================  ========  =======  =============  ========  ===========  ============================================================
  Variable Name                       Type      Units    Constraints    Required  Default      Notes
  ==================================  ========  =======  =============  ========  ===========  ============================================================
  ``foundationType``                  string             See [#]_       Yes                    Type of foundation 
  ``foundationPerimeter``             double    m                       No                     Foundation perimeter
  ``foundationFloorArea``             double    m2                      No                     Foundation floor area                     
  ``foundationWallHeight``            double    m                       No                     Foundation total wall height (slab to ceiling)     
  ``foundationWallDepth``             double    m                       No                     Foundation wall depth (slab to grade)    
  ``foundationWallInsulation``        double    RSI                     No                     Foundation wall effective insulation value 
  ``foundationSlabInsulation``        double    RSI                     No                     Foundation slab effective insulation value
  ==================================  ========  =======  =============  ========  ===========  ============================================================

  .. [#] ``foundationType`` choices are "basement", "crawlspace", "slab-on-grade", "walkout", and "piers"


Systems
-------





Occupant Characteristics
------------------------





