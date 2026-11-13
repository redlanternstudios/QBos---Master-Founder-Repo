# Claudex Handoff — SightEngine Image Intelligence
**Date:** 2026-11-13  
**From:** Ro / ChatGPT working session  
**Destination:** Claudex (Claude + Codex shared brain)  
**Related PR:** https://github.com/redlanternstudios/QBos---Master-Founder-Repo/pull/45  
**Canonical implementation package:** `redlanternstudios/QBos---Master-Founder-Repo/packages/sight-engine/`

## 1. Why this work exists

Ro identified that website imagery can make otherwise sophisticated websites feel generic, template-driven, or AI-generated. In the Bele Law website preview, the layout and typography were strong, but individual images felt independently sourced: generic gavel/legal stock imagery, disconnected photographic styles, predictable Statue of Liberty imagery, and inconsistent lighting/color/composition.

The goal is not to apply one filter to every image. The goal is to make each image look authentic, intentional, contextually relevant, and naturally integrated into its page.

## 2. Product decision

Extend the existing QuietBuild OS SightEngine package into **SightEngine Image Intelligence™**, reusable across RedLantern Studios products and client websites.

Initial consumers discussed:
- Bele Law
- Mahmood Ebrahim Real Estate
- HireWire
- Authentic Hadith
- Future RedLantern products and client projects

This is an extension of the existing SightEngine package, not a new disconnected engine or a Bele Law-only implementation.

## 3. Existing verified repository baseline

Repository inspection found:
- Package: `packages/sight-engine/`
- Existing files: `src/types.ts`, `src/validator.ts`, `src/index.ts`, package README.
- Existing capabilities include quality tiers A/B/C, asset metadata/spec types, resolution/camera/lighting/composition/video/logo validation, quality scoring, AI-artifact checks, and prompt-header generation.
- Existing monorepo references include a SightEngine adapter, Supabase migration/schema references, and proof-harness route.
- Current package is primarily a visual-quality validation library. The new 16-engine image lifecycle capabilities are a proposed extension and must not be represented as already implemented.

Important design correction: camera/lens/bit-depth metadata can be useful when supplied for original photography or production assets, but must not be mandatory for ordinary web photos, stock imagery, illustrations, or screenshots.

## 4. Current specification artifacts

A documentation-only branch and PR were created:
- Branch: `docs/sightengine-image-intelligence`
- PR #45: https://github.com/redlanternstudios/QBos---Master-Founder-Repo/pull/45
- Files:
  - `packages/sight-engine/docs/IMAGE_INTELLIGENCE_MASTER_SPEC.md`
  - `packages/sight-engine/templates/IMAGE_INTELLIGENCE_PROJECT_TEMPLATE.md`
  - `packages/sight-engine/README.md` (adds a clearly labeled specification/roadmap section)

PR #45 is OPEN and NOT MERGED. It contains documentation only; no runtime code or schema was changed.

## 5. Sixteen-engine target architecture

1. Image Discovery — finds/ranks candidates by context, relevance, rights, and composition.
2. Image Provenance — tracks source, creator, licensing, attribution, origin, and derivatives.
3. Image Perception — analyzes subject, composition, lighting, color, and technical condition.
4. Brand-Aware Art Direction — evaluates fit against brand/page/section context.
5. Image Enhancement — deterministic, non-destructive corrections using tools such as Sharp.
6. Image Composition — focal points, crop geometry, safe zones, aspect ratios, viewport-specific framing.
7. Background Integration — restrained gradients, scrims, edge transitions, blending where appropriate.
8. Responsive Image — desktop/tablet/mobile art direction and delivery.
9. Visual Consistency — compares image sets across pages without forcing identical style.
10. Image Authenticity — combines provenance and cautious anomaly signals; never claims certainty from pixels alone.
11. Image Quality Assurance — technical, visual, rights, accessibility, and configured publication gates.
12. Image Asset Management — centralized project-aware library, versions, derivatives, permissions.
13. Generation & Editing Orchestration — provider adapters, references, provenance, cost tracking, approval.
14. Performance Optimization — formats, variants, compression, caching, CDN, loading.
15. Visual Regression — viewport screenshots and before/after layout/image comparison.
16. Creative Review — human approval, rejection, revision, override, and audit history.

A central orchestrator coordinates these as logical modules. Do not prematurely split them into 16 microservices.

## 6. Core technical decisions

- Preserve existing SightEngine public APIs and consumers.
- Inspect existing repo conventions before adding infrastructure.
- Use Sharp for deterministic processing where appropriate.
- Use Next.js Image in Next.js consumers.
- Keep image components presentation-focused; processing/AI analysis runs server-side or in background jobs.
- Reuse existing Supabase/Postgres/storage architecture where it exists.
- Avoid creating duplicate organization/project/user tables.
- Preserve originals; store derivative lineage and transformation parameters.
- Do not invoke AI on every render.
- Do not invent licensing permissions or infer AI origin with certainty.
- Separate objective technical failures from subjective creative recommendations.
- Build incrementally, test, and report truthful status.

## 7. Brand/art direction profiles

Starter profiles in the spec:
- Premium Editorial
- Luxury Corporate
- Modern Technology
- Luxury Real Estate
- Spiritual Editorial
- Documentary Natural

Profiles are configurable/versioned, not hardcoded. Preserve natural skin tones/materials and avoid forcing brand colors when that damages realism.

## 8. Bele Law pilot context

The existing Bele Law website is the first pilot, not the only target. Preserve the current logo, brand identity, typography, navigation, page architecture, content, and functionality.

The Practice Areas section is the initial image audit. Replace generic legal clichés only through reviewed recommendations. Preferred direction: authentic legal/professional environments, relevant California context, human-centered storytelling, natural light, editorial composition. Avoid generic gavel imagery, repetitive courthouse stock, predictable Statue of Liberty imagery, fake office scenes, and repetitive synthetic visuals.

## 9. Required next actions for Claudex

1. Read the current Claudex bridge and follow the bridge protocol before modifying Claudex memory/state.
2. Review PR #45 and verify the three documentation files.
3. Review the existing SightEngine package, adapter, migration, and proof route against the new blueprint.
4. Produce a gap map: existing/partial/designed-only/missing.
5. Decide where SightEngine image-intelligence work belongs in the active product/lane registry.
6. Create a phased implementation plan preserving the existing API.
7. Do not claim runtime implementation until code and tests prove it.
8. If a lane change or bridge write is required, use the documented bridge command layer and respect current sync color.

## 10. Recent working context

- Ro asked for GitHub/open-source research on making website imagery feel more integrated and less AI-like.
- The earlier research direction identified Sharp, imgproxy, BlurHash, and CSS-based ambient treatments as candidate techniques. Treat these as candidates to evaluate, not dependencies already adopted.
- The chosen implementation starting point is Sharp + Next.js Image, with other dependencies added only when justified.
- The desired result is a reusable visual intelligence capability, not a set of filters or one-off CSS fixes.
- The master specification is a design/engineering blueprint. The next step is repository-level gap analysis, then controlled implementation phases.

## 11. Truth boundary

Verified in this session:
- The SightEngine package exists in the QBOS master repo.
- Existing validation/types/readme were inspected.
- The documentation branch and PR #45 were created.
- PR is open, not merged.
- No code, migration, or runtime behavior was changed.

Not verified:
- Any of the new 16 engines being implemented.
- Any production image-processing pipeline.
- Any live Bele Law image replacement.
- Any Claudex memory/bridge update.
