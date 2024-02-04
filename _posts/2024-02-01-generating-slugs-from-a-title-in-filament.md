---
title: Generating Slugs from a Title in Filament
author: hamad
date: 2020-03-01 11:33:00 +0800
categories: [Filament, Laravel]
tags: [filament]
pin: true
image:
  path: /assets/img/filament-slugs-featured.webp
---

# Generating Slugs from a Title in Filament

Original Article: [Generating Slugs from a Title in Filament](https://laravel-news.com/generating-slugs-from-a-title-in-filament)

---

Filament is a powerful Laravel admin panel framework that makes building admin interfaces a breeze. In this article, we'll explore how to generate slugs from a title using Filament.

## Introduction

Slugs are user-friendly URL components derived from the title of a resource. They are essential for creating clean and readable URLs. Filament simplifies the process of generating slugs by providing convenient methods.

## Generating Slugs in Filament

Filament uses the `Spatie\Sluggable` package under the hood for slug generation. To use slugs in your Filament models, follow these steps:

### 1. Install Spatie Sluggable Package

Add the Spatie Sluggable package to your Laravel project using Composer:

```bash
composer require spatie/laravel-sluggable
```
