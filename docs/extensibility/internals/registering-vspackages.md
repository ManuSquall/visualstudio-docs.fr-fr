---
title: Inscription des VSPackages | Microsoft Docs
description: Un fichier. pkgdef contient des informations qui, sinon, seraient ajoutées au registre système. Découvrez comment Visual Studio utilise les fichiers. pkgdef pour décrire/localiser un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e2ed8d7c376f7d9f23e06786fefc1a955ebea3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069463"
---
# <a name="registering-vspackages"></a>Inscription de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s’appuie sur des fichiers. pkgdef pour décrire et localiser un VSPackage. Un fichier. pkgdef contient toutes les informations d’inscription qui seraient autrement ajoutées au registre système. Les VSPackages gérés sont enregistrés en ajoutant des attributs au code source, puis en exécutant l' [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sur l’assembly résultant pour générer un fichier. pkgdef.

## <a name="in-this-section"></a>Dans cette section
- [Spécification de l’emplacement du fichier VSPackage au shell Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Décrit le chemin de chargement pour les VSPackages.

- [Inscription et désinscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explique comment inscrire un VSPackage.
