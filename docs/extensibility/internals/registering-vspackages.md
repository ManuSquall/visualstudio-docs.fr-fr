---
title: Enregistrement vsPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705746"
---
# <a name="registering-vspackages"></a>Inscription de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]s’appuie sur des fichiers .pkgdef pour décrire et localiser un VSPackage. Un fichier .pkgdef contient toutes les informations d’enregistrement qui seraient autrement ajoutées au registre du système. Les VSPackages gérés sont enregistrés en ajoutant des attributs au code source, puis en exécutant [l’utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sur l’assemblage résultant pour générer un fichier .pkgdef.

## <a name="in-this-section"></a>Dans cette section
- [Spécification de l’emplacement du fichier VSPackage au shell Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Décrit le chemin de chargement pour VSPackages.

- [Inscription et désinscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explique comment enregistrer un VSPackage.
