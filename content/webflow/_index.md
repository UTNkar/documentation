---
title: "Webflow"
weight: 30
chapter: true
bookCollapseSection: true
author: Ludvig Aldén
---

This guide is designed to help both developers and editors navigate and efficiently use Webflow for managing our website. Given that Webflow's interface and capabilities closely resemble those of HTML and CSS, individuals with background knowledge in these areas will find Webflow particularly intuitive.

The Webflow website was designed and developed by Ludvig Aldén for three months during november 2023–january 2024.

## Understanding Access Modes

Webflow offers two primary modes for website modification:

- **Designer Mode**: This mode is reserved for deep structural and design changes and is accessible exclusively through the [admin@utn.se](mailto:admin@utn.se) Webflow account. It grants full control, allowing users to alter the website's layout, add or modify elements, and adjust styling directly.
- **Editor Mode**: This mode, accessible to up to three additional accounts such as [info@utn.se](mailto:info@utn.se), is tailored for content editing. Users can alter text and images within the predefined structure but cannot change the website's HTML structure or its CSS styling.

## Utilizing Media Queries

Media queries enable the creation of responsive designs that adapt to various screen sizes. In Designer mode, you can select different screen sizes from an option bar at the top. It's crucial to:

- Initially design for the largest screen size.
- Check responsiveness and aesthetics on smaller screens.
- Make necessary adjustments for smaller screens to ensure consistency and usability across devices.

## Localization and Translation

Webflow supports localization—a feature that allows you to cater content to different languages. To translate content:

1. Select the target language from the top left corner.
2. Right-click the element you wish to translate and choose "Translate content".

Be wary of automatic translations, especially for specific terms or names that might not translate accurately (e.g., "Uppsala teknolog- och naturvetarkår"). Manual verification is advised.

## Working with Components

Components in Webflow help avoid repetitive work by allowing you to reuse structures or elements. However, Webflow's components are not as versatile as those in some programming frameworks (like React), with limitations such as:

- Inability to use arrays.
- Lack of support for nesting components within each other.

When components do not meet needs due to these limitations, utilizing CSS classes for styling and structure repetition may be a more effective approach.

## Best Practices and Pitfalls

To maintain the integrity and functionality of the website, adhere to the following guidelines:

- **Variables**: Utilize variables for frequently used values (e.g., color codes) to facilitate easy updates.
- **Style Adjustments**: Prioritize adjustments for the largest screen size first, then refine for smaller screens.
- **Style Resetting**: To revert style changes, reset the property to inherit styles from a less specific selector.
- **Interactions and Animations**: Ensure that interactive elements and animations function correctly and look good in all contexts.
- **Content Consistency**: Regularly update content across all language versions.
- **Correct Class Usage**: Specifically assign "Section" and "Container" classes to their respective elements for proper styling.
- **Component Property Editing**: When using components, edit only their properties to ensure consistent functionality across the site.

## For Those with Limited Experience

If you're less experienced with Webflow or front-end development in general, a safe approach is to duplicate existing elements for new content sections. This method ensures structural consistency and simplifies the editing process.

## Spacing and Aesthetics

Consistency in spacing between elements is key to a cohesive design. Webflow uses "em" units, with "1em" typically equating to "16px". Adjust spacing using predefined classes like "Without Spacing" or "Less Spacing" to achieve the desired look while maintaining uniformity across the site.

## Content Width for Readability

An optimal line length for text readability ranges between 60-90 characters. We standardize content width to `60ch` for paragraphs on desktops, adjusting as necessary on smaller screens to maintain readability and aesthetic consistency.

## Applying Custom CSS

For specific styling needs not covered by Webflow's editor, custom CSS can be applied through an "HTML Embed" element placed in the `Header` component. This ensures the custom styling is applied globally. Exercise caution when using custom CSS and update it across all language versions when necessary.

## Text Casing Guidelines

- **Titles**: Use sentence-case for Swedish titles and Title Case for English titles.
- **List Items**: Always use sentence case, except for proper nouns or specific names.

## Continuous Documentation Updates

Webflow's platform is subject to frequent updates, which may render parts of this documentation obsolete. Contributors are encouraged to revise and update this guide to reflect the most current practices and features.
