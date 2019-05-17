---
title: Inscription de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 426adc0cd150d5867760a8570df5777fec8260a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859258"
---
# <a name="registering-vspackages"></a>Inscription de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s’appuie sur les fichiers .pkgdef pour décrire et de localiser un VSPackage. Un fichier .pkgdef contient toutes les informations d’inscription qui seraient sinon ajoutées dans le Registre système. VSPackages gérés sont inscrits par l’ajout d’attributs au code source, puis en exécutant la [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sur l’assembly résultant pour générer un fichier .pkgdef.

## <a name="in-this-section"></a>Dans cette section
- [Spécification de l’emplacement du fichier VSPackage au shell Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Décrit le chemin d’accès de chargement pour les VSPackages.

- [Inscription et désinscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explique comment inscrire un VSPackage.
