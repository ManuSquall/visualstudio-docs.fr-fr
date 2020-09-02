---
title: Inscription des VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157388"
---
# <a name="registering-vspackages"></a>Inscription de VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s’appuie sur des fichiers. pkgdef pour décrire et localiser un VSPackage. Un fichier. pkgdef contient toutes les informations d’inscription qui seraient autrement ajoutées au registre système. Les VSPackages gérés sont enregistrés en ajoutant des attributs au code source, puis en exécutant l' [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sur l’assembly résultant pour générer un fichier. pkgdef.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Spécification de l’emplacement du fichier VSPackage au shell Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Décrit le chemin de chargement pour les VSPackages.  
  
 [Inscription et désinscription de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explique comment inscrire un VSPackage.  
  
 [Utilisation d’un attribut d’inscription personnalisé pour inscrire une extension](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Décrit comment créer un manifeste d’inscription qui peut être utilisé pour déployer un VSPackage managé.
