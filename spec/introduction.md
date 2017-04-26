---
layout: default
title: Introduction
---

Introduction to CpML
====================

The Commodities product Mark-up Language (CpML) is the commodity trading
industry standard that enables the representation of trades and other
related information in a standardized way. The standard is widely used
for electronic confirmation of Over-The-Counter (OTC) trades and for
regulatory reporting in Europe.

CpML defines the data format that is used by the following processes:

-   eCM (electronic Confirmation Matching)

-   eRR (electronic Regulatory Reporting)

-   eXRP (eXchange-Related Processes)

<!--<img src="media/image1.jpeg" width="622" height="402" />

The CpML standard itself is process-neutral. The data structure is
defined using XML schemas (XSD). Market participants deliver XML
documents that base on these schemas and are called CpMLDocuments. For
each process, there is a different standard that defines how the data is
processed and which CPML structures are used. <span id="_Toc474941567"
class="anchor"></span>

1.  About this Document
    ===================

2.  Revision History
    ----------------

|             |                 |                                                                                                                                    |                          |
|-------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| **Version** | **Date**        | **Changes**                                                                                                                        | **Author of changes**    |
| 4.1         | April 2012      | Alignment with GTRfC FpML Message Specification v1.7.                                                                              
                                                                                                                                                                     
                                 Addition of Physical Oil, Bullion.                                                                                                  
                                                                                                                                                                     
                                 Enhancement of Physical Electricity and Coal to account for US products.                                                            | EFET                     |
| 4.2         | October 2012    | Alignment with GTRfC FpML Message Specification v1.7.3.1                                                                           
                                                                                                                                                                     
                                 Addition of strategies, cross asset class products and introduced the ‘Generic Confirmation’ for non-standard products.             | EFET                     |
| 4.2d        | October 2012    | Addition of Cancellation document.                                                                                                 | EFET                     |
| 4.2e        | November 2012   | Clarifications to the CpMLReportingEnvelope                                                                                        | EFET                     |
| 4.2f        | December 2012   | Implementation clarifications and minor adjustments to business rules for Calculation Periods                                      | EFET                     |
| 4.2g        | January 2013    |                                                                                                                                    | EFET                     |
| 4.2g        | December 2013   |                                                                                                                                    | CpML Technical Committee |
| 5.1         | November 2013   |                                                                                                                                    | CpML Technical Committee |
| 5.2         | February 2014   |                                                                                                                                    | CpML Technical Committee |
| 5.3         | November 2015   | REMIT Phase 1 and ESMA Level 2                                                                                                     | CpML Technical Committee |
| 6.1         | January 2016    | Requirements from users                                                                                                            
                                                                                                                                                                     
                                 Versioning amended to be in line with CpML Organisation versioning                                                                  | CpML Technical Committee |
| 6.2         | February 2016   | Changes for REMIT Phase 2                                                                                                          | CpML Technical Committee |
| 6.3         | March-July 2016 | Consistency check between schema and CpML description. Overview of changes:                                                        
                                                                                                                                                                     
                                 -   Alignment of document structure with schema structure, i.e. sections added or removed, tables merged, order of fields adapted.  
                                                                                                                                                                     
                                 -   Usage types corrected.                                                                                                          
                                                                                                                                                                     
                                 -   Names and descriptions corrected.                                                                                               
                                                                                                                                                                     
                                 -   Missing fields, field types and value types added.                                                                              
                                                                                                                                                                     
                                 -   Redundant tables and sections removed.                                                                                          
                                                                                                                                                                     
                                 -   Key/Info column removed.                                                                                                        
                                                                                                                                                                     
                                 -   Process-specific information removed.                                                                                           
                                                                                                                                                                     
                                 -   Consistent terminology and spelling of terms.                                                                                   
                                                                                                                                                                     
                                 -   Rules for modal verbs added and modal verbs corrected.                                                                          
                                                                                                                                                                     
                                                                                                                                                                  
                                 -   payload document = transaction details section                                                                                  
                                                                                                                                                                     
                                 -   envelope = regulatory details                                                                                                   
                                                                                                                                                                     
                                 -   Conventions to explain document usage added.                                                                                    |                          |
| 6.4         | February 2017   | -   Additional time stamp fields to compensate for DLS issues                                                                      
                                                                                                                                                                     
                                 -   ‘EURegulatoryDetails/Formula­ProductInformation/Underlying’ changed to mandatory                                                
                                                                                                                                                                     
                                 -   New units of measure added for quantities                                                                                       
                                                                                                                                                                     
                                 -   Amended for EMIR RTS/ITS                                                                                                        
                                                                                                                                                                     
                                 -   Removed ERR-specific rules and enrichment information                                                                           |                          |
| 6.4.1       | April 2017      | Minor corrections:                                                                                                                 
                                                                                                                                                                     
                                 -   Value “O” for ‘ActionType’ removed.                                                                                             
                                                                                                                                                                     
                                 -   Length of ‘ClassificationOfProductType’ set to “255”.                                                                           
                                                                                                                                                                     
                                 -   Value “OT” for ‘EProduct1CodeType’ removed.                                                                                     
                                                                                                                                                                     
                                 -   Value “SB” for ‘EProduct2CodeType’ added.                                                                                       
                                                                                                                                                                     
                                 -   Type “ContractTypeType” added to chapter 8.                                                                                     
                                                                                                                                                                     
                                 -   Type “LoadDeliveryIntervalType” changed from hours only to hours:minutes (e.g. 08:00).                                          |                          |

<span id="_Toc474941569" class="anchor"><span id="_Toc435719072" class="anchor"></span></span>Purpose and Scope
---------------------------------------------------------------------------------------------------------------

This document contains the specification of the CpML standard. The CpML
standard defines the vocabulary for exchanging standardized messages for
commodity trading and reporting processes.

The CpML specification corresponds to the underlying XML schemas, which
implement this specification. The XML schemas define the data structures
and rules for the following document types:

1.  CpMLDocument: Market participants generate messages with trade
    information in a standardized format, the so-called CpMLDocument.

2.  StrategyConfirmation: Combines fundamental transaction types in
    order to describe a trading strategy.

The CpML specification defines a generic vocabulary that can be applied
to different business processes. Process-relevant information is
described in the corresponding process specifications, for example, the
eCM standard.

Target Audience
---------------

This document is for business analysts and IT professionals in the
commodity trading business who want to provide standardized trade
information in the CpML format for post-trade data processing.

For example, this can be:

-   Software engineers and data architects who implement CPML interfaces

-   Business analysts who develop process interfaces

The following knowledge is assumed:

-   Familiarity with the terms and processes used in the commodity
    trading industry

-   Know-how regarding the structure and functionality of XML schemas

Additional Information
----------------------

This section lists web sites or documents with additional information
related to the CpML standard.

| **Ref ID**                                          | **Description**                                                    | **Source**                                                                                        |
|-----------------------------------------------------|--------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| 1.  <span id="_Ref454200837" class="anchor"></span> | List of codes specific to EFET and CPML, for example, broker codes | <http://www.efet.org/Standardisation/Static-data>                                                 |
| 1.  <span id="_Ref454200634" class="anchor"></span> | Esma register of Regulated Markets                                 | <http://registers.esma.europa.eu/publication/searchRegister?core=esma_registers_mifid_rma>        |
| 1.  <span id="_Ref456779450" class="anchor"></span> | Home page of CpML standard                                         | <http://cpml.org>                                                                                 |
| 1.  <span id="_Ref454200766" class="anchor"></span> | Incoterm rules, published by the Internation Chamber of Commerce   | <http://www.iccwbo.org/incoterms/id3042/index.html>                                               |
| 1.  <span id="_Ref454201047" class="anchor"></span> | Full list of BSC (Balancing and Settlement Code) signatories       | <https://www.elexon.co.uk/bsc-related-documents/bsc-signatories-qualified-persons>                |
| 1.  <span id="_Ref454201394" class="anchor"></span> | Coal quality specifications as listed in SCoTA                     | <http://www.globalcoal.com/scota/scotaSpecs.cfm>                                                  |
| 1.  <span id="_Ref455157935" class="anchor"></span> | FpML<sup>®</sup> (Financial products Markup Language) web site     | [www.fpml.org](http://www.fpml.org)                                                               |
| 1.  <span id="_Ref456363049" class="anchor"></span> | EIC codes published by ENTSO-E                                     | <https://www.entsoe.eu/data/energy-identification-codes-eic/eic-documentation/Pages/default.aspx> |
| 1.  <span id="_Ref458522546" class="anchor"></span> | Acer Transaction Reporting User Manual                             | <https://www.acer-remit.eu/portal/public-documentation>                                           |
| 1.                                                  |                                                                    |                                                                                                   |
| 1.                                                  |                                                                    |                                                                                                   |

1.  Conventions
    -----------

2.  ### Use of Modal Verbs

For compliance with the CPML standard, implementers need to be able to
distinguish between mandatory requirements, recommendations and
permissions, as well as possibilities and capabilities. This is
supported by the following rules for using modal verbs.

The key words “must”, “must not”, “required”, “should”, “should not”,
“recommended”, “may” and “optional” in this document are to be
interpreted as follows:

| **Key word** | **Description**                                                                                                                                                                                                                                                                                                                             |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Must         | Indicates an absolute requirement. Requirements must be followed strictly in order to conform to the standard. Deviations are not allowed.                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                                                                             
                Alternative expression: required, is mandatory                                                                                                                                                                                                                                                                                               |
| Must not     | Indicates an absolute prohibition. This phrase means that the provision must not be used in any implementation of the CPML standard.                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                                                                                             
                Alternative expression: must be omitted                                                                                                                                                                                                                                                                                                      |
| Should       | Indicates a recommendation. Among several possibilities, one is recommended as particularly suitable, without mentioning or excluding others. There may exist valid reasons in particular circumstances to ignore a particular item, but the full implications must be understood and carefully weighed before choosing a different course. 
                                                                                                                                                                                                                                                                                                                                                             
                Alternative expression: recommended                                                                                                                                                                                                                                                                                                          |
| May          | Indicates a permission. This word means that an item is truly optional within the limits of CPML. One data supplier may choose to include the item because a particular transaction requires it or because the data supplier feels that it enhances the document while another data supplier may omit the same item.                        
                                                                                                                                                                                                                                                                                                                                                             
                Alternative expression: optional                                                                                                                                                                                                                                                                                                             |
| Should not   | This phrase means that there may exist valid reasons in particular circumstances when the particular behavior is acceptable or even useful, but the full implications should be understood and the case carefully weighed before implementing any behavior described with this label.                                                       
                                                                                                                                                                                                                                                                                                                                                             
                Alternative expression: “not recommended”                                                                                                                                                                                                                                                                                                    |

### Typographical Conventions

This documentation uses the following typographical conventions:

-   ‘AgentID’: single quotation marks are used to indicate field names.

-   “trader”: double quotation marks are used to indicate field values.

-   Reporting/Europe: Slashes are used to indicate paths or nested nodes
    within the schema, for example, ….

-   TotalVolumeUnit: Field names and values as well as attributes are
    consistently written with camel case spelling, as in the schema.
    There are no spaces between words and each new word starts with an
    uppercase letter.

### <span id="_Ref456250853" class="anchor"><span id="_Toc474941575" class="anchor"></span></span>Notation of Schema

The CpMLDocument schema reference in section 5 is a flat representation
of the tree structure in the corresponding XSD schema.

For each main node in the schema, there is a separate section with a
table that contains the sections and fields in that node. The fields are
listed in the same order as in the schema.

Subsections are indicated with a gray background. The start and end of
each section is clearly indicated. Subsections are nested within each
others.

For each field, you find information about the usage type, see section
4.5.4, and the business rules. These rules determine the dependencies on
other fields or values, where applicable.

Fields and value types are reused in different locations of the schema.
Therefore, the general field descriptions and value type descriptions
are described in separate sections in alphabetical, see sections 7 and
8. <span id="_Ref456250396" class="anchor"></span>

### <span id="_Ref456951351" class="anchor"><span id="_Toc474941576" class="anchor"></span></span>Information on Field Usage

Information on mandatory or optional use of a field is specified in
column “Usage”:

-   **O = Optional**. These fields are logically optional and not
    required by business rules. The information may be present in
    the CpMLDocument.

-   **C = Conditional**. These fields are logically conditional, meaning
    the field must be provided if and only if the specified conditions
    are met.

-   **M = Mandatory**. Mandatory fields are logically required and must
    always be present, unless the parent field may be omitted.

-   **M+C = Mandatory with condition**. Fields with this condition are
    logically required. According to the business rules, specific values
    must be set if the specified conditions are met.

-   **M+CH = Mandatory, but part of a choice**. One of the fields in an
    XSD choice section must be provided. Thus, all fields within the
    choice are marked as mandatory in the schema.

### Information on Field Occurrence

If nothing else is stated for a field, the following rules apply with
regard to the minimum or maximum occurrence of the field:

-   Conditional or optional fields: (0-1)  
    These fields can be absent or occur exactly once within the
    given context.

-   Mandatory fields: (1-1)  
    These fields must occur exactly once within the given context.

In all other cases, the allowed number of repetitions is clearly
indicated. Examples: (0-n) or (1‑4).

<span id="_Ref447175198" class="anchor"><span id="_Ref447557284" class="anchor"><span id="_Toc474941578" class="anchor"><span id="_Toc70378618" class="anchor"><span id="_Ref105218252" class="anchor"><span id="_Ref105218271" class="anchor"><span id="_Toc179107761" class="anchor"></span></span></span></span></span></span></span>CPMLDocument IDs
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

To provide a common syntax for CPMLDocuments that is comprehensible and
maintains uniqueness, the ID in the ‘DocumentID’ field must be unique.
It is recommended to use the following syntax:

1.  Document type abbreviation (e.g. “CNF” for TradeConfirmation)

2.  Date code (8 characters, in yyyymmdd format)

3.  Locally and daily unique transaction identifier of the sender

4.  @

5.  Sender identification, i.e. domain name or party code of the sender

Examples:

-   CNF\_20040610\_1234567890@electrabel.com

-   CAN\_20040610\_1234567890@11XELECTRABEL—Z

**Important:** The document ID must not exceed a total length of 50
characters.

**Important:** Once created, the document ID must not be changed any
more. To retransmit information about the same transaction, the version
ID must be changed instead.

<span id="_Ref456250810" class="anchor"><span id="_Toc474941579" class="anchor"><span id="_Ref377556768" class="anchor"></span></span></span>CpMLDocument Schema Reference
==========================================================================================================================================================================

The CpMLDocument extends the basic trade description structure of CpML
to include support for reporting of regulatory, transaction and position
data on a per-jurisdiction basis. The CpMLDocument comprises one
specific section with regulatory details per reporting regime. In
addition to the regulatory sections, the CpMLDocument includes one or
more transaction details sections, for example, with Trade Confirmation
or Broker Confirmation information, and other supporting information
such as images of paper confirmations or other binary files.

Each CpMLDocument contains information about exactly one transaction and
is not used to combine information from multiple transactions.

**Note:** For more information about the notation of the schema, see
section 4.5.3.


-->
