---
layout: default
title: Europe
---

# Europe
### Europe

This section contains the fields that are used for European Regulatory Reporting under the EMIR and REMIT regimes.

<table frame="all" cols="4" colsep="1" rowsep="1">
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Usage</strong></th>
<th><strong>Type</strong></th>
<th><strong>Business Rule</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td colspan="4"><p><strong>Reporting/Europe</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If the trade described in the CpMLDocument is reported for EMIR or REMIT, then this section is mandatory.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td colspan="4"><strong>Europe/ProcessInformation</strong>: mandatory section</td>
</tr>
<tr class="odd">
<td>Reporting­Role</td>
<td>M+C</td>
<td>ReportingRole­Type</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “Clearing_Agent”, then the transaction details section must be ‘ETDTradeDetails’.</p></li>
<li><p>If the transaction being reported is an intra-group transaction that is reported on behalf of another group entity and the reporting entity is a party to the transaction, then the ‘ReportingRole’ should be set to “CP_Agent”.</p></li>
<li><p>If the reporting entity is not a party to the transaction, that is, the trade is between two other group entities or a group entity and an external organisation or two external organisations, then the ‘ReportingRole’ must be set to “Internal_Agent”.</p></li>
</ul>
<p><strong>Important:</strong> “CP_Agent” or “Clearing_Agent” must be a party to the transaction described in the transaction details section.<br />
“Internal_Agent” or “Execution_Agent” must not be a party to the transaction described in the transaction details section.</p></td>
</tr>
<tr class="even">
<td>EMIRReport­Mode</td>
<td>M</td>
<td>ReportMode­Type</td>
<td></td>
</tr>
<tr class="odd">
<td>REMITReport­Mode</td>
<td>M</td>
<td>ReportMode­Type</td>
<td></td>
</tr>
<tr class="even">
<td>Position</td>
<td>C</td>
<td>TrueFalse­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If the transaction details section is ‘ETDTradeDetails’, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul>
<p><strong>Values:</strong></p>
<ul>
<li><p>If the transaction details section describes a position, then this field must be set to “True”.</p></li>
<li><p>If the transaction details section describes an individual transaction, then this field must be set to “False”.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Backload</td>
<td>M+C</td>
<td>TrueFalseType</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If the CpMLDocument is to be treated as back-loaded information, then this field must be set to “True”.</p></li>
<li><p>Else, this field must be set to “False”.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Execution</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence/Values:</strong></p>
<ul>
<li><p>If the CpMLDocument describes a trade that is treated as an Execution under REMIT Phase 2, then this field is mandatory and must be set to “True”.</p></li>
<li><p>Else, this field must be set to “False” or be omitted.</p></li>
<li><p>If ‘Execution’ is “True”, then ‘Backload’ must be set to “False” and at least one ‘LinkedTransactionID’ must be present and the transaction details section must be ‘TradeConfirmation’ with ‘Agent’ section where ‘AgentType’ is set to “Broker”.</p></li>
</ul>
<p><strong>Note:</strong> If this field is omitted from the input CpMLDocument, then the value is considered to be “False” for REMIT processing. For EMIR processing, the field is ignored.</p></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>ProcessInformation</strong></td>
</tr>
<tr class="even">
<td colspan="4"><strong>Europe/Action:</strong> mandatory section</td>
</tr>
<tr class="odd">
<td>ActionType</td>
<td>M+C</td>
<td>Action­Type­Type</td>
<td><p>Determines the type of report, for example, a new report or a contract termination.</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>If the transaction details section is ‘ETDTradeDetails’ and the CpMLDocument is the first occurrence of the UTI, then this field must be set to “N” or “P”.</p></li>
<li><p>If the transaction details section is not ‘ETDTradeDetails’ and the CpMLDocument is a first-time submission of a derivative transaction or post-trade event, then this field must be set to “N” (New).</p></li>
<li><p>If ‘Backload’ is set to “True”, then this field must be set to “N” (New). This ensures that any back-loaded report is loaded as a new action.</p></li>
<li><p>If the CpMLDocument is a modification of a previously reported derivative contract that is common to both counterparties (bilateral change), then this field must be set to “M” (Modify).</p></li>
<li><p>If the CpMLDocument is a correction of a previously reported transaction without a modification of the trade details (unilateral change), then this field must be set to “R” (Revision).</p></li>
<li><p>If the CpMLDocument is a nullification or an early termination of an existing contract, then this field must be set to “C” (Cancel).</p></li>
<li><p>If the CpMLDocument is a removal of a wrongly submitted report, then this field must be set to “E” (Error).</p></li>
<li><p>If the CpMLDocument is a compression of a previously reported contract, then this field must be set to “Z”.<br />
For ETDs that were previously reported with ‘ActionType’ set to “P”, the value “Z” may not be used to report the compression of the exchange-traded derivative into a position. This would be an unrequired repetition of the previous report, which already incorporated the compression of the ETD into a position.</p></li>
</ul></td>
</tr>
<tr class="even">
<td  colspan="4">End of <strong>Action</strong></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>Europe/EURegulatoryDetails</strong>: mandatory section</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “Trader”, “CP_Agent” or “Clearing_Agent”, then this section must be completed from the perspective of the sender.</p></li>
<li><p>If ‘Sender ID’ is set to “BuyerParty”, then the sender is the buyer.</p></li>
<li><p>If ‘Sender ID’ is set to “SellerParty”, then the sender is the seller.</p></li>
<li><p>If ‘ActingOnBehalfOf’ is set to “Buyer”, then this section must be completed from the perspective of the ‘BuyerParty’ in the transaction details section.</p></li>
<li><p>If ‘ActingOnBehalfOf’ is set to “Seller”, then this section must be completed from the perspective of the ‘SellerParty’ in the transaction details section.</p></li>
<li><p>If ‘ActingOnBehalfOf’ is set to “Buyer_And_Seller”, then this section must be completed from the perspective of the ‘BuyerParty’ in the transaction details section.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>UTI</td>
<td>O</td>
<td>UTIType</td>
<td></td>
</tr>
<tr class="odd">
<td>Repository</td>
<td>O</td>
<td>Repository­Type</td>
<td></td>
</tr>
<tr class="even">
<td>Reporting­Timestamp</td>
<td>O</td>
<td>UTCTime­stamp­Type</td>
<td></td>
</tr>
<tr class="odd">
<td>TraderUser­Name</td>
<td>C</td>
<td>NameType</td>
<td><p>The identifier of the counterparty trader (reporting side) who initiates the trade event on the platform where the trade is booked.</p>
<p>If the trade is not executed through an OMP, then the Market Participant must supply this data.</p></td>
</tr>
<tr class="even">
<td>CPFinancial­Nature</td>
<td>O</td>
<td>CP­Financial­Nature­Type</td>
<td></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>EURegulatoryDetails/CPSectors</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “F” or “N”, then this section is optional.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>CPSector</td>
<td>M</td>
<td>Corporate­Sector­Type</td>
<td><p>Repeatable field (1-n)</p>
<p><strong>Repetitions:</strong></p>
<ul>
<li><p>If more than one value is reported, then there must be one ‘CPSector’ field for each value.</p></li>
</ul>
<p><strong>Values:</strong></p>
<ul>
<li><p>Each ‘CPSector’ field must contain a different value. If ‘CPFinancialNature’ is set to “F”, then this field must contain one of the following values: “A”, “C”, “F”, “I”, “L”, “O”, “R” or “U”.</p></li>
<li><p>If ‘CPFinancialNature’ is set to “N”, then this field must contain one of the following values: “1”, “2”, ..., “21”.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td  colspan="4">End of <strong>CPSectors</strong></td>
</tr>
<tr class="even">
<td>Beneficiary­ID</td>
<td>C</td>
<td>PartyType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘TradingCapacity’ is set to “A”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Trading­Capacity</td>
<td>O</td>
<td>Trading­Capacity­Type</td>
<td></td>
</tr>
<tr class="even">
<td>OtherCP­Country</td>
<td>O</td>
<td>Country­Code­Type</td>
<td></td>
</tr>
<tr class="odd">
<td>Commercial­OrTreasury</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “N”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Clearing­Threshold</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “N”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Collateral­isation</td>
<td>O</td>
<td>Collaterali­sation­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “F”, “N”, or “O”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Collateral­isation­Portfolio</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Collateralisation’ is set to any other value than “U”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
<li></li>
</ul></td>
</tr>
<tr class="odd">
<td>Collateral­isation­Portfolio­Code</td>
<td>C</td>
<td>Portfolio­Code­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CollateralisationPortfolio’ is set to “False”, then this field must be omitted.</p></li>
<li><p>Else, this field is optional.</p></li>
</ul></td>
</tr>
<tr class="even">
<td colspan="4"><p><strong>EURegulatoryDetails/ReportingOnBehalfOf</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ differs from “Trader”, then this section is mandatory.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>ActingOn­BehalfOf</td>
<td>M</td>
<td>OnBehalfOf­Type</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “CP_Agent” or “Clearing_Agent” or if ‘ETDTradeDetails/ReportingRole’ is set to “Internal_Agent”, then this field must not contain the value “Buyer_And_Seller”.<br />
The reason is that the counterparty agent or clearing agent must be a party to the transaction that is reported (see ‘AgentID’).<br />
In the case of an ETD, the “Internal_Agent” cannot know the identity of the other counterparty since the trade is cleared and anonymous.</p></li>
</ul>
<p>Rules for ‘SenderID’ in transaction details section:</p>
<ul>
<li><p>If ‘ReportingRole’ is set to “Internal_Agent” and ‘ActingOnBehalfOf’ is set to “Buyer” or “Buyer_And_Seller”, then ‘SenderID’ must be equal to ‘BuyerParty’.</p></li>
<li><p>If ‘ReportingRole’ is set to “Execution_Agent” and the transaction details section is not ‘ETDTradeDetails’ and ‘ActingOnBehalfOf’ is set to “Buyer” or “Buyer_And_Seller”, then ‘SenderID’ must be equal to ‘BuyerParty’.</p></li>
<li><p>If ‘ReportingRole’ is set to “Internal_Agent” and ‘ActingOnBehalfOf’ is set to “Seller”, then ‘SenderID’ must be equal to ‘SellerParty’.</p></li>
<li><p>If ‘ReportingRole’ is set to “Execution_Agent” and the transaction details section is not ‘ETDTradeDetails’ and ‘ActingOnBehalfOf’ is set to “Seller”, then ‘SenderID’ must be equal to ‘SellerParty’.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>AgentID</td>
<td>M+C</td>
<td>PartyType</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “CP_Agent” or “Clearing_Agent” or ‘ETDTradeDetails/ReportingRole’ is set to “Execution_Agent”, then ‘AgentID’ must be equal to ‘SenderID’.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>ReportingOnBehalfOf/OtherCounterpartyDetails</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “Execution_Agent” or “InternalAgent” and ‘ActingOnBehalfOf’ is set to “Buyer_And_Seller”, then this section is mandatory and must refer to the ‘SellerParty’ in the transaction details section.</p></li>
<li><p>If ‘ReportingRole’ is set to “CP_Agent” or “Clearing_Agent” and ‘ActingOnBehalfOf’ is set to “Buyer”, then this section is mandatory and must refer to the ‘BuyerParty’ in the transaction details section.</p></li>
<li><p>If ‘ReportingRole’ is set to “CP_Agent” or “Clearing_Agent” and ‘ActingOnBehalfOf’ is set to “Seller”, then this section is mandatory and must refer to the ‘SellerParty’ in the transaction details section.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>TraderUser­Name</td>
<td>O</td>
<td>NameType</td>
<td><p>The Market Participant must supply this data for trades not executed through an OMP.</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “Execution_Agent”, then this field should contain the log on identity of the trader on the execution platform.</p></li>
<li><p>If ‘ReportingRole’ is set to “CP_Agent”, then this field should contain an identification of the other counterparty trader who initiates the lifecycle event that is reported.</p></li>
<li><p>If ‘ReportingRole’ is set to “Internal_Agent”, then this field should contain an identification of the other counterparty trader who initiates the lifecycle event that is reported.</p></li>
<li><p>If ‘ReportingRole’ is set to “Clearing_Agent”, then this field should contain an identification of the other counterparty trader who initiates the lifecycle event that is reported.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Repository</td>
<td>O</td>
<td>Repository­Type</td>
<td><p>The trade repository for EMIR reporting.</p>
<p><strong>Note:</strong> This field is not used by eRR when processing CpML submissions for REMIT.</p></td>
</tr>
<tr class="even">
<td>CPFinancial­Nature</td>
<td>O</td>
<td>CP­Financial­Nature­Type</td>
<td></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>OtherCounterpartyDetails/CPSectors</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “F” or “N”, then this section is mandatory.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>CPSector</td>
<td>O</td>
<td>Corporate­Sector­Type</td>
<td><p>Repeatable field (1-n)</p>
<p><strong>Repetitions:</strong></p>
<ul>
<li><p>If more than one value is reported, then there must be one ‘CPSector’ field for each value.</p></li>
</ul>
<p><strong>Values:</strong></p>
<ul>
<li><p>Each ‘CPSector’ field must contain a different value.</p></li>
<li><p>If ‘CPFinancialNature’ is set to “F”, then this field must contain one of the following values: “A”, “C”, “F”, “I”, “L”, “O”, “R” or “U”.</p></li>
<li><p>If ‘CPFinancialNature’ is set to “N”, then this field must contain one of the following values: “1”, “2”, ..., “21”.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>CPSectors</strong></td>
</tr>
<tr class="even">
<td>Beneficiary­ID</td>
<td>C</td>
<td>PartyType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘TradingCapacity’ is set to “A”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Trading­Capacity</td>
<td>O</td>
<td>Trading­Capacity­Type</td>
<td></td>
</tr>
<tr class="even">
<td>Other­CP­Country</td>
<td>O</td>
<td>Country­Code­Type</td>
<td></td>
</tr>
<tr class="odd">
<td>Commercial­Or­Treasury</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “N”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Clearing­Threshold</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “N”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Collateral­isation</td>
<td>O</td>
<td>Collaterali­sation­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CPFinancialNature’ is set to “F”, “N”, or “O”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Collateral­isation­Portfolio</td>
<td>C</td>
<td>TrueFalseType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Collateralisation’ is set to any other value than “U”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
<li></li>
</ul></td>
</tr>
<tr class="odd">
<td>Collateral­isation­Portfolio­Code</td>
<td>C</td>
<td>Portfolio­Code­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘CollateralisationPortfolio’ is set to “False”, then this field must be omitted.</p></li>
<li><p>Else, this field is optional.</p></li>
</ul></td>
</tr>
<tr class="even">
<td colspan="4">End of <strong>OtherCounterpartyDetails</strong></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>ReportingOnBehalfOf</strong></td>
</tr>
<tr class="even">
<td colspan="4"><strong>EURegulatoryDetails/ProductIdentifier</strong>: optional section</td>
</tr>
<tr class="odd">
<td>Product­Identification­Type</td>
<td>C</td>
<td>IdentificationOf­Product­Type­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘VenueOfExecution’ is set to “XOFF”, then this field is mandatory.</p></li>
<li><p>If ‘VenueOfExecution’ contains a MIC code classified as ISIN or Aii in the MiFID database (see ref ID [2]), then this field is mandatory.</p></li>
<li><p>If ‘VenueOfExecution’ contains a MIC code that is either unclassified or classified as neither ISIN nor Aii in the MiFID database (see ref ID [2]), then this field must be omitted.</p></li>
<li><p>If ‘VenueOfExecution’ is set to “XXXX”, then this field must be omitted.</p></li>
</ul>
<p><strong>Values:</strong></p>
<ul>
<li><p>If ‘VenueOfExecution’ is set to “XOFF”, then this field must be set to “I”.</p></li>
<li><p>If ‘VenueOfExecution’ contains a MIC code classified as ISIN, then this field must be set to “I”.</p></li>
<li><p>If ‘VenueOfExecution’ contains a MIC code classified as Aii, then this field must be set to “A”.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Product­Identification</td>
<td>C</td>
<td>IdentificationOfProduct­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ProductIdentificationType’ is present, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul>
<p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ProductIdentificationType’ is set to “I”, then this field must contain the ISIN for the traded product.</p></li>
<li><p>If ‘ProductIdentificationType’ is set to “A”, then this field must contain the Aii for the traded product.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Product­Classification­Type</td>
<td>M</td>
<td>Classification­OfProduct­TypeType</td>
<td><ul>
<li></li>
</ul></td>
</tr>
<tr class="even">
<td>Product­Classification</td>
<td>M+C</td>
<td>Classification­OfProduct­Type</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ProductClassificationType’ is set to “C”, then this field must contain a CFI representing the traded product.</p></li>
<li><p>If ‘ProductClassificationType’ is set to “U”, then this field must contain the UPI of the traded product.<br />
<strong>Important:</strong> Until a mechanism for UPI generation has been defined, the CFI mechanism is used in all cases.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4"><strong>ProductIdentifier/EProduct</strong>: mandatory section</td>
</tr>
<tr class="even">
<td>EProductID1</td>
<td>M</td>
<td>EProduct1­Code­Type</td>
<td></td>
</tr>
<tr class="odd">
<td>EProductID2</td>
<td>M</td>
<td>EProduct2­Code­Type</td>
<td></td>
</tr>
<tr class="even">
<td  colspan="4">End of <strong>EProduct</strong></td>
</tr>
<tr class="odd">
<td  colspan="4">End of <strong>ProductIdentifier</strong></td>
</tr>
<tr class="even">
<td>­ContractType</td>
<td>C</td>
<td>­Contract­Type­Type</td>
<td><p><strong>Occurrence and Values:</strong></p>
<ul>
<li><p>If the transaction is a leg of a physical swap executed under a single contract, then this field is mandatory and must be set to “SW”.</p></li>
<li><p>If the transaction is a leg of a spread that is executed under a single contract, then this field is mandatory and must be set to “SP”.</p></li>
<li><p>For all other types of transactions, including the legs of a physical swap or spread that are executed under separate contracts, this field is optional.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>EURegulatoryDetails/LinkedTransactionInformation</strong>: optional section</p>
<p>This section indicates if two transactions are linked to each other or to transactions executed within the framework of non-standard contracts linked to the contract.</p>
<p>The ‘LinkedTransactionInformation’ section must be used in the following scenarios:</p>
<p>When a trade occurs across multiple products due to the nature of the product, for example, a product that is a spread of two or more products falling under the scope of REMIT. The trade for each product must be reported and the different trades must be linked to each other.</p>
<p>Usage scenarios:</p>
<ul>
<li><p>Clean and Dirty Spark Spreads: a trade that involves electricity and gas. The two contracts are reported separately: one leg for the electricity and one leg for the gas trade. The two legs must be linked using this field.</p></li>
<li><p>Physical Swap: a trade that involves two gas or electricity trades. A geographical physical swap involves two trades: selling gas in a particular delivery point and buying it in another delivery point. If the trades are executed simultaneously, both trades must be reported separately and linked using this field.</p></li>
<li><p>When a transaction is executed within the framework of a non-standard contract. The details of the transaction specifying at least an outright volume and price must be reported and linked to the non-standard contract ID.</p></li>
<li><p>When a trade occurs due to a set of orders or a linked order, such as a block order or a linked order within a single product.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Linked­Trans­action­ID</td>
<td>M+C</td>
<td>UTIType</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If the linked trades are standard trades, then the value must be identical to the UTI of the linked trade.</p></li>
<li><p>If the linked trades are non-standard trades, then the value must be identical to the non-standard contract ID.</p></li>
</ul>
<p>Repeatable field: (1-n)</p></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>LinkedTransactionInformation</strong></td>
</tr>
<tr class="even">
<td>TradeID</td>
<td>M</td>
<td>TradeIDType</td>
<td><p>The internal trade ID of the counterparty reporting the transaction.</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>If ‘ReportingRole’ is set to “Execution_Agent”, then this field must be set to the transaction ID that the platform assigns to the buyer and the seller side of the transaction because the internal trade ID of the counterparty is not known to the execution agent.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>VenueOf­Execution</td>
<td>M</td>
<td>VenueOf­Execution­Type</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If this transaction is executed on a Regulated Market or MTF, then this field must contain the MIC code of the venue.</p></li>
<li><p>If the transaction is a listed derivative executed on a venue that is not a Regulated Market or MTF, then this field must be set to “XOFF”.</p></li>
<li><p>Else, this field must be set to “XXXX”.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Compression</td>
<td>O+C</td>
<td>TrueFalseType</td>
<td><p><strong>Values:</strong></p>
<ul>
<li><p>If the transaction is the result of compression, then this field must be set to “True”.</p></li>
<li><p>Else, this field must be set to “False”.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4"><p>Start of conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If there is an upfront payment to report, then this section is mandatory.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>UpFront­Payment</td>
<td>M</td>
<td>PriceType</td>
<td></td>
</tr>
<tr class="odd">
<td>Upfront­Payment­Currency</td>
<td>M</td>
<td>Currency­Code­Type</td>
<td></td>
</tr>
<tr class="even">
<td colspan="4">End of conditional section</td>
</tr>
<tr class="odd">
<td>Execution­Timestamp</td>
<td>O</td>
<td>UTC­Timestamp­Type</td>
<td>The time of entry into the system of record of the reporting counterparty or of the agent reporting on behalf of the reporting counterparty.</td>
</tr>
<tr class="even">
<td>Master­Agreement­Version</td>
<td>O</td>
<td>Master­Agreement­Version­Type</td>
<td>The vintage of the agreement under which the reported transaction is executed.</td>
</tr>
<tr class="odd">
<td>Clearing­Obligation</td>
<td>O</td>
<td>TrueFalseType</td>
<td></td>
</tr>
<tr class="even">
<td>Intragroup</td>
<td>M</td>
<td>TrueFalseType</td>
<td></td>
</tr>
<tr class="odd">
<td>LoadType</td>
<td>C</td>
<td>LoadTypeType</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>Transaction details section is ‘TradeConfirmation’:</p></li>
<li><p>If ‘TransactionType’ is set to “FOR”, “OPT”, “PHYS_INX” or “OPT_PHYS_INX” and ‘Commodity’ is set to “Power” or “Gas”, then this field is mandatory.</p></li>
<li><p>If ‘TransactionType’ is a Financial Transaction, then the following applies:</p>
<ul>
<li><blockquote>
<p>If ‘EURegulatory­Details/Formula­Product­Information/Commodity­Detail’ is set to “EL” or “NG”, then this field is optional.</p>
</blockquote></li>
<li><blockquote>
<p>If ‘TradeConfirmation/FloatPriceInformation[1‑2]/<br />
Commodity­Reference[1-n]/IndexCommodity’ is set to “Electricity” or “Nat_Gas”, then this field is optional.</p>
</blockquote></li>
</ul></li>
<li><p>Else, this field must be omitted.</p></li>
<li></li>
</ul></td>
</tr>
<tr class="even">
<td>Confirmation­Means</td>
<td>M</td>
<td>Confirmation­Means­Type</td>
<td>Indicates whether the contract was electronically confirmed, non-electronically confirmed or remains unconfirmed.</td>
</tr>
<tr class="odd">
<td>Confirmation­Timestamp</td>
<td>C</td>
<td>UTC­Timestamp­Type</td>
<td><p>The date and time of the confirmation of the transaction as defined under Commission Delegated Regulation No 149/2013 (1) indicating the time zone in which the confirmation has taken place.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ConfirmationMeans’ is set to “N”, then this field must be omitted.</p></li>
<li><p>Else, this field is mandatory.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Notional­Amount</td>
<td>C</td>
<td>Price­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>Transaction details section is ‘TradeConfirmation’:</p></li>
<li><p>If ‘TransactionType’ is set to “PHYS_INX” or “OPT_PHYS_INX”, then this field is mandatory.</p></li>
<li><p>If ‘TransactionType’ is set to “FLT_SWP” and at least one of the ‘FloatPriceInformation’ sections has multiple ‘CommodityReference’ sections, then this field is mandatory.</p></li>
<li><p>If ‘TransactionType’ is set to “FLT_SWP” and at least one of the ‘FloatPriceInformation’ sections has a ‘SpreadRate’ field, then this field is mandatory.</p></li>
<li><p>Else, this field is optional.</p></li>
</ul>
<p><strong>Important:</strong> The ‘NotionalAmount’ is always in the major currency unit, for example, GBP (Pound Sterling) not GBX (Pence Sterling) .</p></td>
</tr>
<tr class="odd">
<td>Early­Termination­Date</td>
<td>C</td>
<td>DateType</td>
<td><p>The termination date of the reported contract.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ActionType’ is set to “C” or “Z”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>IndexValue</td>
<td>O</td>
<td>QuantityType</td>
<td>If known, the value of the fixing index at execution or the offset (‘SpreadAmount’) to the fixing index agreed at execution.</td>
</tr>
<tr class="odd">
<td>Complex­TradeID</td>
<td>O</td>
<td>Complex­TradeIDType</td>
<td></td>
</tr>
<tr class="even">
<td>Report­Tracking­Number</td>
<td>C</td>
<td>Report­Tracking­Number­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If the transaction details section is ‘ETDTradeDetails’ and ‘ActionType’ is set to “P” or “Z”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>EURegulatoryDetails/SettlementDates</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If the transaction details section is ‘TradeConfirmation’ and ‘TransactionType’ is set to “FOR” or “PHYS_INX”, then this section is mandatory.</p></li>
<li><p>If the transaction details section is ‘ETDTradeDetails’, then this section is mandatory.</p></li>
<li><p>If the transaction details section is ‘IRSTradeDetails’ and TransactionType is set to “FXD_SWP”, “FXD_FXD_SWP” or “FLT_SWP”, then this section is mandatory.</p></li>
<li><p>Else, this section is optional.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>DateOf­Settlement</td>
<td>M</td>
<td>DateType</td>
<td><p>Repeatable field: (1-n)</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>If multiple settlement dates exist for the transaction, the final settlement date must be used.</p></li>
<li><p>For OTC swaps and physical forwards, the last date of settlement of the derivative contract must be used.</p></li>
<li><p>For options, the premium payment date must be used.</p></li>
<li><p>For exchange-traded derivatives, the following applies: ‘DateOfSettlement’ is the greater of the maturity date or the cease date.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>SettlementDates</strong></td>
</tr>
<tr class="even">
<td colspan="4"><p><strong>EURegulatoryDetails/ETDProductInformation</strong>: optional section</p>
<p>This section may contain explicit values derived from ETD product definitions.</p></td>
</tr>
<tr class="odd">
<td>Underlying­Code­Type</td>
<td>C</td>
<td>Underlying­Code­Type­Type</td>
<td><p><strong>Occurrence &amp; Values:</strong></p>
<ul>
<li><p>If ‘VenueOfExecution’ is set to “XOFF” and ‘ETDTradeDetails/PrimaryAssetClass’ is set to “ForeignExchange” or “Commodity”, then this field is mandatory and must be set “I”.</p></li>
<li><p>If ‘VenueOfExecution’ is set to a MIC code that is listed in the MiFID database and for which an instrument identifier is specified, then this field is mandatory and must be set to “I” or “A”, depending on the relevant instrument classification scheme.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Underlying</td>
<td>C</td>
<td>Underlying­Type</td>
<td><p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘UnderlyingCodeType’ is present, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Notional­Currency1</td>
<td>M</td>
<td>Currency­Code­Type</td>
<td>The currency of the notional amount. In the case of an interest rate derivative contract, this is the notional currency of leg 1.</td>
</tr>
<tr class="even">
<td>Notional­Currency2</td>
<td>C</td>
<td>Currency­Code­Type</td>
<td><p><strong>Occurrence &amp; Values:</strong></p>
<ul>
<li><p>If the transaction is an interest-rate derivative contract, then this field is mandatory and must be equal to the notional currency of leg 2.</p></li>
<li><p>Else, this field is optional.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Deliverable­Currency</td>
<td>M</td>
<td>Currency­Code­Type</td>
<td>The currency to be delivered.</td>
</tr>
<tr class="even">
<td>Price­Notation</td>
<td>M</td>
<td>Price­Notation­Type</td>
<td>The manner in which the price is expressed.</td>
</tr>
<tr class="odd">
<td>Price­Multiplier</td>
<td>M</td>
<td>QuantityType</td>
<td><p>The number of units of the financial instrument that are contained in a trading lot.</p>
<p>Example: the number of derivatives represented by one contract.</p></td>
</tr>
<tr class="even">
<td>Total­Volume­Quantity­Unit</td>
<td>C</td>
<td>UnitOf­Measure­Type</td>
<td><p>The unit of measure used.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “Commodity”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Delivery­Type</td>
<td>M</td>
<td>Settlement­Type</td>
<td>Indicates whether the contract is settled physically or in cash.</td>
</tr>
<tr class="even">
<td>Effective­Date</td>
<td>M</td>
<td>DateType</td>
<td></td>
</tr>
<tr class="odd">
<td>Maturity­Date</td>
<td>M</td>
<td>DateType</td>
<td>The original date of expiry of the reported contract. An early termination must not be reported in this field.</td>
</tr>
<tr class="even">
<td>Commodity­Base</td>
<td>C</td>
<td>Commodity­Base­Type</td>
<td><p>The type of commodity underlying the contract.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “Commodity”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Commodity­Detail</td>
<td>C</td>
<td>Commodity­Detail­Type</td>
<td><p>Details of the ‘CommodityBase’.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “Commodity”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Delivery­Point­Or­Zone</td>
<td>C</td>
<td>AreaType</td>
<td><p>The delivery points of market areas.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETD­Product­Information/CommodityDetail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Intercon­nection­Point</td>
<td>C</td>
<td>AreaType</td>
<td><p>The borders or border points of a transportation contract.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETD­Product­Information/CommodityDetail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>LoadType</td>
<td>C</td>
<td>LoadTypeType</td>
<td><p>The product delivery profile of the delivery periods of a day.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETD­Product­Information/Commodity­Detail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Duration</td>
<td>C</td>
<td>DurationType</td>
<td><p>The full period of the notional or physical delivery period.</p>
<p>The value is always the largest unit that can be expressed as an integer.</p>
<p>Examples:</p>
<ul>
<li><p>If the duration is two weeks, the value must be “W” (week).</p></li>
<li><p>If the duration is five weeks, the value must be “M” (month).</p></li>
<li><p>If the duration is four months, the value must be “Q” (quarter).</p></li>
</ul>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETD­Product­Information/CommodityDetail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td colspan="4"><p><strong>ETDProductInformation/LoadDeliverySchedule</strong>: conditional, repeatable section (0-n)</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETDProductInformation/CommodityDetail’ is set to “NG” or “EL”, then this section is mandatory.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul>
<p><strong>Repetitions:</strong></p>
<p>For each delivery schedule pattern, one ‘LoadDeliverySchedule’ section must be present.</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>The schedules described in the ‘LoadDeliverySchedule’ sections may not overlap in terms of times or days of the week. Each time schedule must start after the end of the previous time schedule. For each day of the week, there may only be one schedule, for example, there may not be one schedule for Mondays and another for weekdays.</p></li>
<li><p>Continuous delivery schedules with whole day deliveries must be described as follows: one ‘LoadDelivery­Schedule’ with one ‘LoadDeliveryInterval’ indicating the start time. Examples: Gas Day or base load.</p></li>
</ul>
<p>Examples:</p>
<ul>
<li><p>To indicate the Gas Day in UK, set ‘DaysOfTheWeek’ to “WD WN”, and add one ‘LoadDeliveryInterval’ field with the value “05:00”.</p></li>
</ul>
<ul>
<li><p>To indicate an off-peak load, add two ‘LoadDeliverySchedule’ sections:</p></li>
</ul>
<ul>
<li><p>[1]: Set ‘DaysOfTheWeek’ to “WD” and add four ‘LoadDeliveryInterval’ fields with the following values: “00:00”, “08:00”, “20:00” and “24:00”.</p></li>
<li><p>[2]: Set ‘DaysOfTheWeek’ to “WN” and add one ‘LoadDeliveryInterval’ field with the value “00:00”.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Load­Delivery­Interval</td>
<td>M</td>
<td>Load­Delivery­IntervalType</td>
<td><p>Repeatable field: (1-n)</p>
<p>The time interval for each block or shape in the local time of the delivery point or zone. The time intervals must be listed in ascending order.</p>
<p>The time intervals are indicated in pairs, marking the start and end time of an interval.</p>
<p>To indicate a complete day, it is sufficient to add a start time, which then corresponds to a 24 hour day. In this case, values less than or equal to 12:00 indicate a positive offset of the delivery schedule in relation to midnight. Values greater than 12:00 indicate a negative offset of the delivery schedule in relation to midnight. See also ‘DeliveryStartDate’ and ‘DeliveryEndDate’.</p></td>
</tr>
<tr class="even">
<td>DaysOfThe­Week</td>
<td>M</td>
<td>DOWType</td>
<td><p>The days of the week of the delivery. Multiple values can be used to indicate multiple days of the week, for example, “MO WE FR” for Mondays, Wednesdays and Fridays.</p>
<p>For each day of the week, there may only be one load delivery schedule.</p></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>LoadDeliverySchedule</strong></td>
</tr>
<tr class="even">
<td>Contract­Capacity</td>
<td>C</td>
<td>QuantityType</td>
<td><p>The quantity per delivery time interval.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETDProduct­Information/Commodity­Detail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Energy­Quantity­Unit</td>
<td>C</td>
<td>UnitOf­Measure­Type</td>
<td><p>A daily or hourly quantity of the underlying commodity.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETDProduct­Information/­CommodityDetail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Delivery­Start­Date­</td>
<td>C</td>
<td>DateType</td>
<td><p>The start date of delivery.</p>
<p>For physically delivered products, this is the start of the physical delivery. For non-delivered products, this is the start of the notional delivery.</p>
<p><strong>Note:</strong> For deliveries that are offset from midnight by a positive or negative number of hours as indicated in the ‘LoadDeliveryInterval’ field, the ‘DeliveryStartDate’ field must contain the date compliant with the market convention as described in the ETD product description.</p>
<p>Examples:</p>
<ul>
<li><p>The delivery schedule for the UK Electricity Day begins at 23:00 in local time, which represents a negative offset of one hour to the delivery start date. The physical delivery begins on 31 March 2017 at 23:00. ‘DeliveryStartDate’ is set to “2017-04-01” and ‘LoadDeliveryInterval’ is set to “23:00”.</p></li>
</ul>
<p>The delivery schedule for the UK Gas Day begins at 05:00 in local time, which represents a positive offset of five hours to the delivery start date. The physical delivery begins on 01 April 2017 at 05:00. ‘DeliveryStartDate’ is set to “2017-04-01” and ‘LoadDeliveryInterval’ is set to “05:00”.<strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/ETDProduct­Information/­CommodityDetail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Delivery­End­Date­</td>
<td>C</td>
<td>DateType</td>
<td><p>The end date of delivery.</p>
<p>For physically delivered products, this is the end of the physical delivery. For non-delivered products, this is the end of the notional delivery.</p>
<p><strong>Note:</strong> For deliveries that are offset from midnight by a positive or negative number of hours as indicated in the ‘LoadDeliveryInterval’ field, the ‘DeliveryEndDate’ field must contain the date compliant with the market convention as described in the ETD product description.</p>
<p>Examples:</p>
<ul>
<li><p>The delivery schedule for the UK Electricity Day ends at 23:00 in local time, which represents a negative offset of one hour to the delivery end date. The physical delivery ends on 30 April 2017 at 23:00. ‘DeliveryEndDate’ is set to “2017-04-30” and ‘LoadDeliveryInterval’ is set to “23:00”.</p></li>
</ul>
<p>The delivery schedule for the UK Gas Day ends at 05:00 in local time, which represents a positive offset of five hours to the delivery start date. The physical delivery ends on 01 May 2017 at 05:00. ‘DeliveryEndDate’ is set to “2017-04-30” and ‘LoadDeliveryInterval’ is set to “05:00”.<strong>Occurrence: </strong></p>
<ul>
<li><p>If ‘Reporting/Europe/EURegulatoryDetails/­ETDProduct­Information/­CommodityDetail’ is set to “NG” or “EL”, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Currency2</td>
<td>C</td>
<td>Currency­Code­Type</td>
<td><p>The cross currency, if different from the currency of delivery.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “ForeignExchange” and the cross currency differs from ‘DeliverableCurrency’, then this field is mandatory.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Exchange­Rate1</td>
<td>C</td>
<td>PriceType</td>
<td><p>The contractual rate of exchange of the currencies.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “ForeignExchange”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Exchange­Rate­Basis</td>
<td>C</td>
<td>QuoteBasis­Type</td>
<td><p>The quote base for an exchange rate.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “ForeignExchange”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>FixedRate­OfLeg2</td>
<td>C</td>
<td>QuantityType</td>
<td><p>The fixed rate of leg 2, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>FixedRate­Day­CountLeg1</td>
<td>C</td>
<td>Day­Count­Fraction­Type</td>
<td><p>The actual number of days in the relevant fixed rate payer calculation period, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>FixedRate­Day­CountLeg2</td>
<td>C</td>
<td>Day­Count­Fraction­Type</td>
<td><p>The actual number of days in the relevant fixed rate payer calculation period, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>FixedLeg­Payment­Frequency­Leg1­</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The frequency of payments for leg 1 of the fixed rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>FixedLeg­Payment­Frequency­Leg2­</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The frequency of payments for leg 2 of the fixed rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Floating­Rate­Payment­Frequency­­Leg1­</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The frequency of payments for leg 1 of the floating rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Floating­Rate­Payment­Frequency­­Leg2</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The frequency of payments for leg 2 of the floating rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Floating­Rate­Reset­Frequency­­Leg1­</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The reset frequency of leg 1 of the floating rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Floating­Rate­Reset­Frequency­Leg2­</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The reset frequency of leg 2 of the floating rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Floating­Rate­Of­Leg1</td>
<td>C</td>
<td>RateIndex­Type</td>
<td><p>The interest rate of leg 1 that is reset at predetermined intervals by reference to a market reference rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Floating­Rate­Reference­Period­Leg1</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The period of the interest rate of leg 1 that is reset at predetermined intervals by reference to a market reference rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Floating­RateOfLeg2</td>
<td>C</td>
<td>RateIndex­Type</td>
<td><p>The interest rate of leg 2 that is reset at predetermined intervals by reference to a market reference rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Floating­Rate­Reference­Period­Leg2</td>
<td>C</td>
<td>Frequency­Period­Type</td>
<td><p>The period of the interest rate of leg 2 that is reset at predetermined intervals by reference to a market reference rate, if applicable.</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If ‘ETDTradeDetails/PrimaryAssetClass’ is set to “InterestRate”, then this field is optional.</p></li>
<li><p>Else, this field must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td colspan="4">End of <strong>ETDProductInformation</strong></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>EURegulatoryDetails/FormulaProductInformation</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>If the transaction details section is ‘TradeConfirmation’ and contains a ‘FloatPriceInformation/FormulaID’ field, then this section is mandatory.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Underlying</td>
<td>M</td>
<td>Underlying­Type</td>
<td>The underlying must be identified with a unique identifier. In case of baskets or indices, an indication for this basket or index must be used if no unique identifier exists.</td>
</tr>
<tr class="odd">
<td>Commodity­Base</td>
<td>M</td>
<td>Commodity­Base­Type</td>
<td>The type of commodity underlying the contract.</td>
</tr>
<tr class="even">
<td>Commodity­Detail</td>
<td>M</td>
<td>Commodity­Detail­Type</td>
<td>Details of the ‘CommodityBase’.</td>
</tr>
<tr class="odd">
<td>Index­Currency­Unit</td>
<td>O</td>
<td>Currency­Code­Type</td>
<td>The currency of the notional amount.</td>
</tr>
<tr class="even">
<td colspan="4">End of <strong>FormulaProductInformation</strong></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>EURegulatoryDetails/FinancialDeliveryInformation</strong>: conditional section</p>
<p><strong>Occurrence:</strong></p>
<ul>
<li><p>The transaction details section is ‘TradeConfirmation’ and ‘TransactionType’ is a Financial Transaction:</p></li>
<li><p>If the ‘IndexCommodity’ field contained in any ‘FloatPriceInformation/CommodityReference’ section is set to “Electricity” or “Nat_Gas”, then this section is optional.</p></li>
<li><p>If ‘EURegulatoryDetails/FormulaProductInformation/CommodityDetail’ is set to “EL” or “NG”, then this section is optional.</p></li>
<li><p>Else, this section must be omitted.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Delivery­PointOr­Zone</td>
<td>M</td>
<td>AreaType</td>
<td><p>Repeatable field: (1-n)</p>
<p>The EIC code identifying a delivery location within the EU that relates to the notional delivery.</p></td>
</tr>
<tr class="odd">
<td>Inter­connection­Point</td>
<td>M</td>
<td>AreaType</td>
<td>The EIC code identifying a delivery location within the EU that relates to the notional delivery.</td>
</tr>
<tr class="even">
<td>Quantity­Volume</td>
<td>M</td>
<td>QuantityType</td>
<td><p>The total number of units included in the contract or order.</p>
<p>This is the rate of delivery, that is, a capacity, not a volume of energy delivery.</p></td>
</tr>
<tr class="odd">
<td>Quantity­Volume­Unit</td>
<td>M</td>
<td>UnitOf­Measure­Type</td>
<td>The unit of measure for the ‘QuantityVolume’ field.</td>
</tr>
<tr class="even">
<td>Delivery­StartDate</td>
<td>M</td>
<td>DateType</td>
<td><p>The date is expressed in local time of the delivery point/area.</p>
<p><strong>Note:</strong> For deliveries that are offset from midnight by a positive or negative number of hours as indicated in the ‘LoadDeliveryInterval’ field, the ‘DeliveryStartDate’ field must contain the date compliant with the market convention.</p>
<p>Examples:</p>
<ul>
<li><p>The delivery schedule for the UK Electricity Day begins at 23:00 in local time, which represents a negative offset of one hour to the delivery start date. The physical delivery begins on 31 March 2017 at 23:00. ‘DeliveryStartDate’ is set to “2017-04-01” and ‘LoadDeliveryInterval’ is set to “23:00”.</p></li>
<li><p>The delivery schedule for the UK Gas Day begins at 05:00 in local time, which represents a positive offset of five hours to the delivery start date. The physical delivery begins on 01 April 2017 at 05:00. ‘DeliveryStartDate’ is set to “2017-04-01” and ‘LoadDeliveryInterval’ is set to “05:00”.</p></li>
</ul>
<p>See also BR008.</p></td>
</tr>
<tr class="odd">
<td>Delivery­EndDate</td>
<td>M</td>
<td>DateType</td>
<td><p>The date is expressed in local time of the delivery point/area.</p>
<p><strong>Note:</strong> For deliveries that are offset from midnight by a positive or negative number of hours as indicated in the ‘LoadDeliveryInterval’ field, the ‘DeliveryEndDate’ field must contain the date compliant with the market convention.</p>
<p>Examples:</p>
<ul>
<li><p>The delivery schedule for the UK Electricity Day ends at 23:00 in local time, which represents a negative offset of one hour to the delivery end date. The physical delivery ends on 30 April 2017 at 23:00. ‘DeliveryEndDate’ is set to “2017-04-30” and ‘LoadDeliveryInterval’ is set to “23:00”.</p></li>
<li><p>The delivery schedule for the UK Gas Day ends at 05:00 in local time, which represents a positive offset of five hours to the delivery start date. The physical delivery ends on 01 May 2017 at 05:00. ‘DeliveryEndDate’ is set to “2017-04-30” and ‘LoadDeliveryInterval’ is set to “05:00”.</p></li>
</ul>
<p>See also BR008.</p></td>
</tr>
<tr class="even">
<td>Duration</td>
<td>M</td>
<td>DurationType</td>
<td><p>The full duration of the delivery period.</p>
<p>The value is always the largest unit that can be expressed as an integer.</p>
<p>Examples:</p>
<ul>
<li><p>If the duration is two weeks, the value must be “W” (week).</p></li>
<li><p>If the duration is 5 weeks, the value must be “M” (month).</p></li>
<li><p>If the duration is four month, the value must be “Q” (quarter).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td colspan="4"><p><strong>FinancialDeliveryInformation/LoadDeliverySchedule</strong>: conditional, repeatable section (1-n)</p>
<p>For each delivery schedule pattern, one ‘LoadDeliverySchedule’ section must be present.</p>
<p><strong>Values:</strong></p>
<ul>
<li><p>The schedules described in the ‘LoadDeliverySchedule’ sections may not overlap in terms of times or days of the week. Each time schedule must start after the end of the previous time schedule. For each day of the week, there may only be one schedule, for example, there may not be one schedule for Mondays and another for weekdays.</p></li>
</ul>
<p>Continuous delivery schedules with whole day deliveries must be described as follows: one ‘LoadDelivery­Schedule’ with one ‘LoadDeliveryInterval’ indicating the start time. Examples: Gas Day or base load.Examples:</p>
<ul>
<li><p>To indicate the Gas Day in UK, set ‘DaysOfTheWeek’ to “WD WN”, and add one ‘LoadDeliveryInterval’ field with the value “05:00”.</p></li>
</ul>
<ul>
<li><p>To indicate an off-peak load, add two ‘LoadDeliverySchedule’ sections:</p></li>
</ul>
<ul>
<li><p>[1]: Set ‘DaysOfTheWeek’ to “WD” and add four ‘LoadDeliveryInterval’ fields with the following values: “00:00”, “08:00”, “20:00” and “24:00”.</p></li>
<li><p>[2]: Set ‘DaysOfTheWeek’ to “WN” and add one ‘LoadDeliveryInterval’ field with the value “00:00”.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Load­Delivery­Interval</td>
<td>M</td>
<td>Load­Delivery­IntervalType</td>
<td><p>Repeatable field: (1-n)</p>
<p>The time interval for each block or shape in the local time of the delivery point or zone. The time intervals must be listed in ascending order.</p>
<p>The time intervals are indicated in pairs, marking the start and end time of an interval.</p>
<p>To indicate a complete day, it is sufficient to add a start time, which then corresponds to a 24 hour day. In this case, values less than or equal to 12:00 indicate a positive offset of the delivery schedule in relation to midnight. Values greater than 12:00 indicate a negative offset of the delivery schedule in relation to midnight. See also ‘DeliveryStartDate’ and ‘DeliveryEndDate’.</p></td>
</tr>
<tr class="odd">
<td>DaysOfThe­Week</td>
<td>M</td>
<td>DOWType</td>
<td><p>The days of the week of the delivery. Multiple values can be used to indicate multiple days of the week, for example, “MO WE FR” for Mondays, Wednesdays and Fridays.</p>
<p>For each day of the week, there may only be one load delivery schedule.</p></td>
</tr>
<tr class="even">
<td colspan="4">End of <strong>LoadDeliverySchedule</strong></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>FinancialDeliveryInformation</strong></td>
</tr>
<tr class="even">
<td colspan="4">End of <strong>EURegulatoryDetails</strong></td>
</tr>
<tr class="odd">
<td colspan="4">End of <strong>Europe</strong></td>
</tr>
</tbody>
</table>
