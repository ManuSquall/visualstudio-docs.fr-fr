---
title: Inscription de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 786522d32680a66aa0f74cf0111c3e98708cce91
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727883"
---
# <a name="registering-vspackages"></a>Inscription de VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s’appuie sur les fichiers .pkgdef pour décrire et de localiser un VSPackage. Un fichier .pkgdef contient toutes les informations d’inscription qui seraient sinon ajoutées dans le Registre système. VSPackages gérés sont inscrits par l’ajout d’attributs au code source, puis en exécutant la [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sur l’assembly résultant pour générer un fichier .pkgdef.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Spécification de l’emplacement du fichier VSPackage au shell Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Décrit le chemin d’accès de chargement pour les VSPackages.  
  
 [Inscription et désinscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explique comment inscrire un VSPackage.  
  
 [Utilisation d’un attribut d’inscription personnalisé pour inscrire une extension](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Décrit comment créer un manifeste de l’enregistrement qui peut être utilisé pour déployer un VSPackage managé.

