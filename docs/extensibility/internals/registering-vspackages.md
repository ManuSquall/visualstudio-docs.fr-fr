---
title: "L’inscription de VSPackages | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d580d3d74d8648b7181ac1ca384d3232fa8225b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="registering-vspackages"></a>L’inscription de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]s’appuie sur les fichiers .pkgdef pour décrire et localiser un VSPackage. Un fichier .pkgdef contient toutes les informations d’inscription qui seraient sinon ajoutées dans le Registre système. VSPackages gérés sont inscrits par ajout d’attributs au code source, puis en exécutant la [CreatePkgDef utilitaire](../../extensibility/internals/createpkgdef-utility.md) sur l’assembly résultant pour générer un fichier .pkgdef.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Spécification de l’emplacement du fichier VSPackage au shell Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Décrit le chemin d’accès lors du chargement de VSPackages.  
  
 [Inscription et désinscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explique comment inscrire un VSPackage.  
