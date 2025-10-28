# MyWebsite: Technical Overview

## Introduction

This document provides a technical overview of the `giannihart/MyWebsite` project. It is a web application built with Next.js (App Router), focusing on performance, a clean architecture, and a dynamic user experience. Key architectural principles include a clear separation of concerns, robust server-side form handling, and a component-driven UI.

## Core Technologies

The technology stack is centered around the React ecosystem, chosen for its component-based architecture and strong community support.

{% cardGroup cols=4 gap="md" %}
{% card title="Framework" icon="box" %}
Next.js (App Router)
{% /card %}
{% card title="UI Library" icon="component" %}
React
{% /card %}
{% card title="Styling" icon="palette" %}
Tailwind CSS with `clsx` and `tailwind-merge`.
{% /card %}
{% card title="UI Components" icon="puzzle" %}
Custom components and Radix UI primitives.
{% /card %}
{% card title="Animations" icon="film" %}
Framer Motion for fluid UI animations.
{% /card %}
{% card title="Form Management" icon="file-input" %}
React Hook Form for client-side state and validation.
{% /card %}
{% card title="Schema Validation" icon="shield-check" %}
Zod for type-safe schema definition and validation.
{% /card %}
{% card title="Database" icon="database" %}
Upstash (Redis) for the newsletter service.
{% /card %}
{% /cardGroup %}

## Key Features

{% accordionGroup %}
{% accordion title="Newsletter Subscription" icon="mail" defaultOpen=true %}
The application features a robust newsletter subscription system.

-   **Frontend**: The user-facing form is built with custom UI components and provides real-time, client-side validation using React Hook Form for immediate user feedback.
-   **Backend**: Form submissions are handled by Next.js Server Actions. A Zod schema validates incoming data on the server before persisting new subscriber information to the Upstash Redis database.
-   **State Management**: The UI clearly communicates submission status (e.g., pending, success, error) to the user.
{% /accordion %}
{% accordion title="Dynamic User Interface" icon="sparkles" defaultOpen=true %}
The user experience is enhanced with several dynamic features.

-   **Theming**: Supports light and dark modes, managed by `next-themes`.
-   **Animations**: Framer Motion is used for subtle transitions and animations to create a more responsive and engaging interface.
-   **Custom Components**: Includes a library of custom components, such as `VideoWithPlaceholder`, which provides a loading state for media assets to prevent layout shifts and improve perceived performance.
{% /accordion %}
{% /accordionGroup %}

## Project Structure

The codebase is organized to promote maintainability and scalability.

{% cardGroup cols=3 gap="md" %}
{% card title="/app" icon="folder-root" %}
The core of the Next.js application, containing routes, pages, and layouts.
{% /card %}
{% card title="/components" icon="folder-kanban" %}
Contains reusable React components. A dedicated `/ui` subdirectory holds primitive, application-agnostic components.
{% /card %}
{% card title="/lib" icon="folder-cog" %}
Houses shared utilities, server actions, constants, and configuration. Logic for newsletter subscriptions and Redis database interactions resides here.
{% /card %}
{% /cardGroup %}

## Environment Configuration

The application requires environment variables to connect to external services like Upstash. A startup utility validates the presence of these variables to prevent runtime errors from misconfiguration.

{% steps %}
{% step title="Create Environment File" %}
Create a `.env.local` file in the project root. This file will store your secret credentials and should not be committed to version control.
{% /step %}
{% step title="Add Credentials" %}
Add the necessary credentials for the Upstash Redis database to your `.env.local` file.

```sh {% filename=".env.local" %}
# .env.local
UPSTASH_REDIS_REST_URL="your_upstash_url"
UPSTASH_REDIS_REST_TOKEN="your_upstash_token"
```
{% /step %}
{% /steps %}