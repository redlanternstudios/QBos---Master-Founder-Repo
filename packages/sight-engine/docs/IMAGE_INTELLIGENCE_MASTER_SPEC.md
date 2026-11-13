# SightEngine™ Image Intelligence
## Master Product, Architecture, and Engineering Specification

**Owner:** RedLantern Studios  
**Parent system:** QuietBuild OS / SightEngine  
**Status:** Proposed architecture and implementation blueprint — not a claim that all capabilities are implemented  
**Version:** 1.0

## 1. Mission and principles

Extend the existing SightEngine package from visual-quality validation into reusable image intelligence and art-direction infrastructure across Bele Law, Mahmood Ebrahim Real Estate, HireWire, Authentic Hadith, and future RedLantern projects.

Lifecycle: **Discover → Establish provenance → Perceive → Art direct → Enhance → Compose → Integrate → Deliver → Validate → Review.**

Principles:
1. Do not make every image look the same; make each image belong to its context.
2. Preserve photographic authenticity. Avoid indiscriminate filters, excessive grading, fake grain, and synthetic detail.
3. Prefer deterministic processing for deterministic tasks. AI analyzes/recommends; it is not invoked on every render.
4. Preserve originals and make transformations traceable and reproducible.
5. Never infer licensing rights or photographic authenticity without evidence.
6. Separate technical checks from subjective creative judgments.
7. Preserve human approval for brand-sensitive and public-facing assets.
8. Do not claim implementation merely because a screen, type, or placeholder exists.
9. Sixteen logical engines do not imply sixteen microservices.
10. Maintain backward compatibility with the existing SightEngine public API.

## 2. Existing baseline and extension boundary

The repository already has `packages/sight-engine/` with quality tiers A/B/C, asset specification types, validation and scoring, lighting/composition checks, AI-artifact checks, prompt-header generation, logo requirements, and existing adapter/database references elsewhere in the monorepo.

The current package is primarily a visual-quality validation library. The lifecycle, brand-aware art direction, provenance, processing studio, responsive composition, and visual-regression capabilities below are proposed extensions.

Before implementation, inspect actual source, tests, migrations, adapters, and consumers. Verify every baseline statement. Do not trust old README status labels without source-level proof.

Do not require camera/lens metadata for ordinary website images, stock photography, screenshots, or illustrations. Retain camera metadata when supplied for original photography.

## 3. Sixteen logical engines

Each engine must have a clear responsibility, typed inputs/outputs, dependencies, configuration, errors, logging, versioning, tests, and human overrides where appropriate.

### 01 — Image Discovery Engine
Find and rank candidates for a brand, page, section, subject, and composition. Search existing project assets first; support provider adapters for licensed stock/public-domain sources, user uploads, client photography, and approved generated assets. Rank by relevance, composition, resolution, brand fit, provenance, license suitability, and crop flexibility. Return candidate references, source/license metadata, dimensions, preview, suitability rationale, warnings, and recommended placement. Never claim commercial-use rights without evidence; respect provider terms and API limits.

### 02 — Image Provenance Engine
Track origin, rights, attribution, transformations, and derivatives. Store original asset ID/name, source/provider/URL, creator, license/evidence/restrictions/expiry, acquisition date/method, AI-generation status and available metadata, project associations, and original-to-derivative lineage. Classify as original photography, licensed stock, public domain, user-uploaded, AI-generated, illustration, composite, or unknown. Unknown is valid. Do not infer origin from appearance alone.

### 03 — Image Perception Engine
Analyze subjects, objects, people, buildings, interiors, landscapes, products, landmarks, and embedded text. Analyze composition (focal subject, negative space, balance, symmetry, depth, foreground/background, horizon, text-safe regions), lighting (direction, natural/artificial indicators, warmth, exposure, highlights/shadows/contrast), color (dominant/secondary/accent colors, luminance, saturation, temperature), and condition (blur, noise, compression, pixelation, distortion, clipping, watermarks, artifacts). Return structured results with model/provider/version, timestamp, confidence, and warnings. Uncertain vision inferences must remain labeled uncertain.

### 04 — Brand-Aware Art Direction Engine
Determine whether imagery belongs in a particular brand/page/section/layout. Brand profiles include colors, typography, photography style, subject preferences, lighting, contrast, saturation, texture, composition, aspect ratios, approved references, prohibited styles, and context rules. Starter profiles: Premium Editorial, Luxury Corporate, Modern Technology, Luxury Real Estate, Spiritual Editorial, Documentary Natural. Profiles are configurable/versioned. Evaluate relevance, palette, lighting, composition, tone, context, and surrounding content. Do not force brand colors if natural skin tones/materials/realism would be damaged. Recommend use as-is, light correction, moderate correction, recompose/crop, replace, or commission/generate, with rationale and confidence.

### 05 — Image Enhancement Engine
Perform non-destructive, reproducible corrections: exposure, brightness, contrast, highlights, shadows, white/black point, gamma, white balance, temperature, tint, saturation, vibrance, hue, and channel adjustments. Optional presets: Warm Editorial, Neutral Natural, Soft Cinematic, Architectural Neutral, Muted Luxury, Rich Contrast, Documentary Natural. Optional denoise, sharpening, compression-artifact reduction, resolution enhancement, grain/texture only when explicitly appropriate. Use Sharp for deterministic operations. Preserve originals; record parameters/tool versions; avoid repeated lossy transformations. Distinguish reconstructed AI detail from source detail.

### 06 — Image Composition Engine
Control framing for the actual layout. Support normalized focal points (0–1), crop boundaries, maximum crop, subject/text-safe zones, optional face-aware cropping where appropriate, horizon/landmark preservation, desktop/tablet/mobile crops, and aspect ratios 16:9, 3:2, 4:3, 1:1, 4:5, 3:4, 2:3, custom. Support full-bleed, contained, split, editorial/asymmetric grid, overlap, layered hero, and image/text layouts. Return crop geometry, focal points, ratios, and layout instructions. Never blindly center-crop.

### 07 — Background Integration Engine
Integrate images naturally without disguising them as something else. Support linear/radial gradients, directional scrims, overlays, edge transitions, background-color harmonization, blend modes, and layered compositions. Evaluate edge contrast, tonal discontinuities, text readability, and detail preservation. Do not wash out images or blend when a clean boundary is better.

### 08 — Responsive Image Engine
Deliver correct assets/crops per viewport: desktop, tablet, mobile, high-density. Support separate source images and art direction per viewport, Next.js Image, srcset/sizes, picture/source where appropriate, lazy loading, priority loading for critical hero assets, and aspect-ratio reservation. Do not assume desktop composition works on mobile or send oversized originals to small devices.

### 09 — Visual Consistency Engine
Evaluate image sets across a page/site: lighting, temperature, saturation, contrast, photographic style, texture, composition, subject diversity, image density, repeated metaphors. Detect duplicate stock images, similar compositions, and conflicting styles. Recommend replacements/treatments without forcing identical styles across unrelated pages.

### 10 — Image Authenticity Engine
Assess provenance and possible anomalies without claiming certainty from pixels alone. Use source records, creator metadata, EXIF where available, generation metadata, lineage, and vision-based checks. Flag possible distorted anatomy/geometry/reflections/shadows/perspective, repeated textures, malformed text, impossible architecture, and unnatural materials. Classification: verified source, declared AI-generated, declared composite, unknown origin, potential visual anomaly. Allow human correction. Never label fraudulent or AI-generated solely from low-confidence detection.

### 11 — Image Quality Assurance Engine
Run configurable technical, visual, accessibility, licensing, and brand gates. Technical: dimensions, resolution, aspect ratio, format, file size, compression, color profile, transparency, metadata, broken references. Visual: sharpness, exposure, crop safety, subject visibility, contrast, relevance, anomaly warnings. Accessibility: alt text, decorative semantics, embedded text, text-overlay contrast. Configurable gates: technical, rights, brand, composition, accessibility, human creative approval. Explain failures and distinguish objective failures from subjective recommendations.

### 12 — Image Asset Management Engine
Centralized permission-aware asset library organized by organization/project/brand/site/page/section/category/source/license/approval. Support upload, preview, search, filter, tag, version, duplicate, archive, replace, approve, reuse. Track originals, derivatives, variants, and published usage. Reuse only when licensing permits. Keep private source storage separate from approved public delivery.

### 13 — Generation & Editing Orchestration Engine
Coordinate approved generation/editing providers through adapters. Request fields: project/brand/page/section, subject/intent, art direction/composition, lighting/materials/palette/ratio, reference images, prohibited elements, and new-generation vs editing intent. Separate factual subject references from style references. Track provider/model/version/cost/request/output/provenance/approval. Generated assets enter the same provenance and QA pipelines. No automatic publication unless policy explicitly permits.

### 14 — Image Performance Optimization Engine
Optimize delivery without sacrificing meaningful quality. Use Sharp and Next.js delivery where appropriate. Support AVIF, WebP, JPEG, PNG, and safe SVG. Preserve originals. Measure original/optimized size, compression ratio, delivered dimensions, format, cache behavior, loading, and layout shifts. Support responsive variants, CDN, caching, lazy/priority loading. Sanitize SVG and validate file formats. Avoid repeated optimization.

### 15 — Visual Regression Engine
Protect layouts when imagery changes. Capture approved page states at desktop/tablet/mobile viewports. Compare crops, layout shifts, overflow, missing/broken images, image boundaries, section dimensions, text placement/contrast, responsive behavior. Produce screenshots and reports. Approval or rollback follows project policy. Use stable test data and repeatable viewport settings.

### 16 — Creative Review Engine
Preserve human creative authority. Show original/proposed/processed assets, desktop/mobile previews, provenance, analysis, compatibility, warnings, and history. Actions: approve, reject, request revision, replace, reprocess, adjust crop/focal point, change treatment/profile, override recommendation. Record reviewer, timestamp, comments, approval state, and history. Enforce role permissions.

## 4. Central orchestrator

The orchestrator coordinates engines without duplicating their logic.

Default lifecycle:
1. Receive image requirement.
2. Discover candidate or register supplied asset.
3. Verify provenance/rights.
4. Analyze image.
5. Evaluate brand/page context.
6. Assess authenticity/anomalies.
7. Recommend retain/correct/recompose/replace.
8. Apply approved enhancement.
9. Generate composition and responsive variants.
10. Integrate into page context.
11. Run consistency and QA.
12. Route to human review when required.
13. Optimize and publish approved derivatives.
14. Run visual regression.
15. Record usage and audit history.

Conditional execution is required. Do not rediscover an approved asset, rerun AI analysis on every render, or generate when a crop suffices.

States: REQUESTED, DISCOVERING, ANALYZING, ART_DIRECTING, PROCESSING, COMPOSING, OPTIMIZING, AWAITING_REVIEW, APPROVED, REJECTED, PUBLISHED, FAILED, ARCHIVED.

Support background jobs, retries, timeouts, idempotency, caching, logs, recovery, and approval gates. Never mark complete before success.

## 5. Image Intelligence Studio

Build an internal workspace using existing SightEngine design tokens/components.

Navigation: Overview, Projects, Asset Library, Image Discovery, Image Analysis, Art Direction, Composition Studio, Enhancement Studio, Brand Profiles, Processing Presets, Quality Assurance, Creative Review, Visual Regression, Usage Analytics, Settings.

Overview: total/approved/pending/failed assets, replacements needed, active projects, optimization savings, processing time, activity.

Project workspace: brand profile, website/page inventory, image inventory/requirements, approved/pending assets, QA and consistency reports.

Asset library: grid/list, search/filter, preview, metadata, rights, versions, project relationships, usage.

Analysis workspace: original, subject classification, composition map, palette, lighting, technical quality, anomaly warnings, brand compatibility.

Art direction: choose project/brand/page/section/purpose/profile; compare candidates and alternatives; preview in page context; submit for review.

Composition: crop, focal point, ratio, responsive positioning, overlays, gradients, integration, viewport previews.

Enhancement: original/processed comparison, controls, presets, history, reset-to-original.

Review: queue, reviewer assignment, comments, revisions, approvals, audit history.

## 6. Reusable integration components

Create typed components as appropriate: SmartImage, EditorialImage, HeroImage, BackgroundImage, ImageCard, ImageGallery, ResponsiveImage, ImageWithScrim, ImageComparison, ImagePlaceholder.

Common props: source/asset reference, alt text/decorative flag, ratio, focal point, brand profile, treatment preset, responsive source/crops, overlay, loading/priority.

Components stay presentation-focused. Ingestion, AI analysis, and transformations belong in server-side services/jobs, never render-time components.

## 7. Data architecture

Inspect existing schema/migrations first. Reuse organization/project/user/storage/audit entities. Add only missing logical entities:

image_projects, image_assets, image_sources, image_provenance, image_variants, image_analysis, image_color_profiles, image_composition_profiles, image_brand_profiles, image_art_direction_profiles, image_treatments, image_processing_jobs, image_usage, image_reviews, image_approvals, image_quality_reports, image_generation_requests, image_regression_runs, image_workflow_events.

Relationship: Organization → Project → Brand Profile → Website → Page → Section → Image Asset → Image Variant.

An asset may have many variants and usage locations. Every derivative retains original lineage. Use UUIDs, timestamps, ownership, status/version, foreign keys, indexes, audit history. Enforce organization/project permissions server-side. Keep private originals private and expose only approved derivatives. Do not duplicate existing project/user tables.

## 8. API architecture

Use validated, versioned server-side APIs:

POST /api/image-intelligence/discover  
POST /api/image-intelligence/analyze  
POST /api/image-intelligence/art-direct  
POST /api/image-intelligence/enhance  
POST /api/image-intelligence/compose  
POST /api/image-intelligence/integrate  
POST /api/image-intelligence/optimize  
POST /api/image-intelligence/validate  
POST /api/image-intelligence/generate  
POST /api/image-intelligence/review  
GET /api/image-intelligence/assets  
GET /api/image-intelligence/projects  
GET /api/image-intelligence/jobs/:id  
GET /api/image-intelligence/reports/:id

Require authentication, authorization, rate limits, idempotency for expensive jobs, structured errors, and audit events. Never expose provider credentials to the browser.

## 9. Technical direction

Prefer existing monorepo conventions. Candidate technologies: TypeScript, Sharp, Next.js Image, PostgreSQL/Supabase where already used, existing object storage, vision-capable models for selected analysis, provider adapters for licensed discovery/generation, and unit/integration/API/processing/visual-regression tests.

Do not add a new database, queue, CDN, or microservice without demonstrated need.

## 10. Brand profiles

Profiles are starting points, not hardcoded identities:

- Premium Editorial: authentic photography, natural light, warm highlights, restrained saturation, organic composition, realistic materials, purposeful negative space.
- Luxury Corporate: professional environments, neutral grading, sophisticated contrast, architecture, balanced negative space.
- Modern Technology: contemporary environments, controlled contrast, precise composition, crisp detail, restrained gradients.
- Luxury Real Estate: accurate architectural lines, natural light, realistic interiors/materials, balanced exposure.
- Spiritual Editorial: authentic cultural context, natural materials, restrained ornamentation, respectful storytelling; no generic religious imagery as a substitute for relevance.
- Documentary Natural: minimal processing, realistic colors, natural exposure, authentic environments.

Each brand profile is independently configurable and versioned.

## 11. Security, rights, performance, governance

Validate uploads, reject unsafe formats, enforce size limits, sanitize SVG, restrict private assets, enforce project permissions server-side, preserve license evidence, maintain provenance/history, require configured publication approvals, track generation provider/cost, cache expensive analysis/transforms, avoid repeated lossy transformations, use least privilege, and never expose credentials or private storage identifiers.

## 12. Bele Law pilot

Use the existing Bele Law website as the first pilot, not as a reason to hardcode Bele Law into the engine.

Preserve its logo, brand identity, typography, navigation, content, routes, and functionality.

For each image: record page/section purpose and source/license; analyze subject/composition/lighting/palette/authenticity signals; assess brand/content relevance and responsive crop; recommend retain/correct/recompose/replace; prepare viewport previews; preview in actual page; request approval; record final decision.

Prioritize authentic legal/professional environments, relevant California context, human-centered storytelling, natural light, and editorial composition. Avoid generic gavel clichés, repetitive courthouse imagery, predictable Statue of Liberty imagery, fake legal-office scenes, and repetitive synthetic visuals.

The Practice Areas section is the first pilot. Do not replace imagery automatically.

## 13. Phased implementation

Phase 0 — Repository intelligence: inspect package/source/tests/migrations/adapters/consumers; report baseline and dependencies; no destructive changes.

Phase 1 — Core infrastructure: asset registry, provenance, storage, jobs, Sharp adapter, SmartImage, responsive delivery.

Phase 2 — Perception: metadata, color, composition, lighting, technical quality, structured outputs.

Phase 3 — Art direction: brand/photography profiles, contextual recommendations, compatibility, versioned presets.

Phase 4 — Composition/enhancement: crop editor, focal points, tonal/color corrections, background integration, comparison UI.

Phase 5 — Asset/review: library, rights, version history, approval, project reuse.

Phase 6 — Advanced intelligence: discovery adapters, authenticity signals, generation orchestration, visual consistency, automated QA.

Phase 7 — Performance/regression: delivery optimization, caching, performance reports, screenshot comparison, visual regression.

Phase 8 — Bele Law pilot: page-by-page audit, recommendations, approved changes, responsive verification, evidence report.

Build reviewable increments, not one uncontrolled code-generation pass.

## 14. Acceptance and truthful status

Core acceptance: assets registered/searched; provenance retained; analysis persisted; brand profiles configurable; treatments reproducible/versioned; crops/focal points adjustable; responsive variants generated; previews work; QA reports generated; reviews persisted; originals unchanged; permissions enforced; existing SightEngine API remains compatible; consumers unbroken; tests pass.

Visual acceptance: natural appearance; page-context fit; credible lighting/color; crop preserves subjects; intentional integration; mobile composition works; cohesive without repetition.

Report each capability as IMPLEMENTED, PARTIAL, DESIGNED ONLY, EXTERNAL INTEGRATION REQUIRED, AWAITING HUMAN APPROVAL, or NOT IN SCOPE.

## 15. Required documentation

Create/update:
1. SYSTEM_ARCHITECTURE.md
2. ENGINE_SPECIFICATIONS.md
3. ENGINE_DEPENDENCY_MAP.md
4. DATABASE_SCHEMA.md
5. API_CONTRACTS.md
6. IMAGE_PROCESSING_PIPELINE.md
7. BRAND_PROFILE_SPECIFICATION.md
8. IMAGE_PROVENANCE_SPECIFICATION.md
9. SECURITY_AND_PERMISSIONS.md
10. QUALITY_ASSURANCE_SPECIFICATION.md
11. IMPLEMENTATION_ROADMAP.md
12. BELE_LAW_PILOT_AUDIT.md
13. TESTING_AND_ACCEPTANCE_REPORT.md

Document evidence and actual status. UI placeholders and docs alone do not prove implementation.

## 16. Final principle

SightEngine is reusable visual intelligence infrastructure for RedLantern Studios. Understand the image, brand, page, and composition; recommend the least invasive change that makes the image belong.

**Do not make every image look the same. Make every image look like it belongs.**

**SEE THE IMAGE. UNDERSTAND THE CONTEXT. PERFECT THE COMPOSITION. PRESERVE THE AUTHENTICITY.**
