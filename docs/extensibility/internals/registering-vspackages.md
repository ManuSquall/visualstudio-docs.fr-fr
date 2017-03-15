---
title: "L&#39;enregistrement de packages VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages gérés, l'inscription"
  - "inscription, les VSPackages gérés"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# L&#39;enregistrement de packages VS
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s'appuie sur des fichiers .pkgdef pour décrire et localiser un VSPackage.  Un fichier .pkgdef contient toutes les informations d'inscription devant être ajoutées à la base de registres.  VSPackages managés sont enregistrés en ajoutant des attributs au code source et l'exécution [Utilitaire de CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) sur l'assembly résultant pour générer un fichier .pkgdef.  
  
## Dans cette section  
 [Spécifiant l’emplacement du fichier de package VS à l’interpréteur de commandes de Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Décrit le chemin de chargement pour les VSPackages.  
  
 [Inscription et annulation de l’enregistrement de packages VS](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explique comment inscrire un VSPackage.  
  
 [Utilisation d’un attribut d’inscription personnalisé pour inscrire une extension](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)  
 décrit comment créer un manifeste d'alignement qui peut être utilisé pour déployer un VSPackage managé.