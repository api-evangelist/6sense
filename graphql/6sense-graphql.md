# 6sense GraphQL Schema

This document describes a conceptual GraphQL schema for the 6sense Revenue AI Platform, covering account-based marketing (ABM), intent data, predictive scoring, firmographic and technographic enrichment, people search, segmentation, campaigns, and integrations.

## Overview

6sense provides B2B revenue intelligence through its Signalverse intent graph. The platform surfaces buying signals from anonymous and known accounts, predicts buying stage and profile fit, and orchestrates omnichannel campaigns across digital advertising, email, and sales channels. This GraphQL schema models the core entities and relationships exposed through the 6sense REST APIs and platform data model.

## Source APIs

- Company Identification API — resolve visitor IP to company + buying signals
- Company Firmographics API — enrich account by domain or email
- Lead Scoring API — predictive product-level contact scoring
- Lead Scoring + Firmographics API — combined enrichment and scoring
- People Enrichment API — batch contact profile enrichment
- People Search API — filter-based contact search by domain

## Schema Source

The schema is a conceptual representation derived from the 6sense public API documentation at https://docs.6sense.com/ and https://api.6sense.com/docs/. It is not an officially published GraphQL endpoint.

## Types

### Account Types

- `Account` — core company record resolved from IP or domain
- `AccountDetails` — extended account metadata and enrichment fields
- `AccountSentiment` — aggregated sentiment signals for an account
- `AccountScore` — product-level intent and fit scores
- `AccountProfile` — ideal customer profile fit assessment
- `AccountKeyword` — keyword-level intent signals for an account
- `AccountIntent` — aggregated intent activity for an account

### Intent Types

- `IntentDetails` — detailed intent topic and signal breakdown
- `IntentSignal` — individual intent event or research signal
- `IntentScore` — numeric intent score with context
- `IntentProfile` — multi-product intent profile across topics
- `IntentStage` — stage of intent journey (Awareness, Consideration, Decision)
- `BuyingStage` — 6sense buying stage classification (Target, Awareness, Consideration, Decision, Purchase)

### Segment Types

- `Segment` — named account or contact segment
- `SegmentDetails` — segment configuration, filters, and counts
- `SegmentMember` — account or contact membership record in a segment

### Contact Types

- `Contact` — person / lead record
- `ContactDetails` — enriched contact profile with skills, education, job history
- `ContactVerification` — email verification status and confidence
- `ContactIntent` — intent signals attributed to a contact's company

### Company Types

- `Company` — company entity with firmographic fields
- `CompanyDetails` — full enrichment: SIC, NAICS, headcount, revenue range
- `CompanyFirmographic` — industry, size, geography, and classification fields
- `CompanyTechnographic` — installed technologies detected for a company
- `CompanyKeyword` — research keywords associated with the company

### Campaign Types

- `Campaign` — ABM advertising or nurture campaign
- `CampaignDetails` — targeting, budget, schedule, and creative configuration
- `CampaignAds` — ad units associated with a campaign
- `CampaignImpressions` — impression metrics for a campaign
- `CampaignClicks` — click metrics for a campaign
- `AdDetails` — individual ad creative with performance metrics

### Audience Types

- `Audience` — built audience for targeting
- `AudienceDetails` — audience configuration and match counts
- `AudienceTarget` — target account or contact within an audience

### Prediction Types

- `Prediction` — predictive model output for an account or contact
- `PredictionDetails` — model features, weights, and confidence
- `PredictionModel` — model definition and training metadata

### Keyword / Topic Types

- `KeywordResearch` — keyword research aggregate
- `Topic` — intent topic cluster
- `TopicDetails` — topic definition, related keywords, volume
- `TopicSignal` — individual research signal mapped to a topic

### Suppression Types

- `Suppression` — suppression list definition
- `SuppressedAccount` — account excluded from targeting

### Team / Admin Types

- `Team` — organizational team within the 6sense platform
- `TeamDetails` — team members, roles, and permissions
- `APIKey` — API key metadata (no secret value)
- `Token` — authentication token record

### Integration Types

- `Integration` — generic integration connector record
- `SalesforceIntegration` — Salesforce CRM sync configuration
- `HubSpotIntegration` — HubSpot CRM sync configuration
- `SegmentIntegration` — Segment CDP integration configuration

### Reporting Types

- `Report` — generated analytics report
- `ReportDetails` — report configuration, filters, and output columns
- `Attribution` — revenue or pipeline attribution record

## Queries

- `account(ip: String, domain: String)` — resolve and enrich an account
- `accountIntent(domain: String!, product: String)` — fetch intent signals for an account
- `contact(email: String, linkedinUrl: String, peopleId: String)` — fetch an enriched contact
- `contacts(domain: String!, filters: ContactFilterInput)` — search contacts at a company
- `segment(id: ID!)` — fetch a segment definition and member count
- `segments` — list all segments
- `campaign(id: ID!)` — fetch a campaign with metrics
- `campaigns` — list campaigns
- `prediction(contactEmail: String, domain: String, product: String!)` — fetch predictive score
- `report(id: ID!)` — fetch a report
- `topic(id: ID!)` — fetch an intent topic
- `topics` — list available intent topics

## Mutations

- `createSegment(input: SegmentInput!)` — create a new segment
- `updateSegment(id: ID!, input: SegmentInput!)` — update a segment
- `deleteSegment(id: ID!)` — delete a segment
- `createCampaign(input: CampaignInput!)` — create a campaign
- `updateCampaign(id: ID!, input: CampaignInput!)` — update a campaign
- `addSuppression(input: SuppressionInput!)` — add account to suppression list
- `removeSuppression(accountId: ID!)` — remove account from suppression list

## References

- https://docs.6sense.com/
- https://api.6sense.com/docs/
- https://support.6sense.com/docs/6sense-api-overview
