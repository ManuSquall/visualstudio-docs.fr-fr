---
title: "Proc&#233;dure&#160;: cr&#233;ation manuelle d’un package d’extension (d&#233;ploiement&#160;VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Proc&#233;dure&#160;: cr&#233;ation manuelle d’un package d’extension (d&#233;ploiement&#160;VSIX)
Vous pouvez créer un package VSIX pour encapsuler une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour le déploiement. Il existe trois façons de créer un package :  
  
-   Créez un projet de package VSIX avec l’un des modèles d’extensibilité inclus dans le Kit de développement logiciel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(SDK\). Pour la plupart des scénarios, il s’agit de l’option la plus simple.  
  
-   Encapsulez la sortie de votre projet d’extension dans un [projet VSIX](../extensibility/vsix-project-template.md) vide. Cette option est recommandée pour les modèles, les assemblys non pris en charge et les types personnalisés.  
  
-   Créez manuellement un package VSIX. Cette option est recommandée uniquement quand les deux autres options ne sont pas disponibles.  
  
 Ce document aborde la troisième option.  
  
## Création d’un package VSIX  
 Pour créer manuellement un package d’extension, ajoutez un fichier extension.manifest et un fichier \[Content\_Types\].xml au projet d’extension. Placez\-les dans un fichier compressé avec votre sortie de génération, puis renommez le fichier compressé pour que son extension de nom de fichier soit .vsix. Le type de l’extension doit être pris en charge par le [schéma VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
>  Les noms des fichiers des packages VSIX ne doivent pas comprendre d’espaces ni de caractères réservés pour les URI, selon la norme [\[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### Pour créer manuellement un package VSIX  
  
1.  Créez une extension Visual Studio d’un type pris en charge par le schéma VSIX.  
  
2.  Créez un fichier XML, puis nommez\-le `extension.vsixmanifest`.  
  
3.  Remplissez le fichier extension.vsixmanifest selon le schéma VSIX. Pour obtenir un exemple de manifeste, consultez [PackageManifest Element \(Root Element, VSX Schema\)](http://msdn.microsoft.com/fr-fr/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4.  Créez un deuxième fichier XML, puis nommez\-le `[Content_Types].xml`.  
  
5.  Remplissez le fichier \[Content\_Types\].xml, comme spécifié dans [La Structure de la Content\_types\] .xml fichier](../Topic/The%20Structure%20of%20the%20Content_types].xml%20File.md).  
  
6.  Placez les deux fichiers XML dans un répertoire avec l’extension à déployer.  
  
     Dans le cas d’un modèle de projet ou d’un modèle d’élément, placez le fichier .zip qui contient le modèle dans le même dossier que les fichiers XML. Ne placez pas les fichiers XML dans le fichier .zip.  
  
     Dans tous les autres cas, placez les fichiers XML dans le même répertoire que la sortie de génération.  
  
7.  Dans l’Explorateur Windows, cliquez avec le bouton droit sur le dossier qui contient le contenu de l’extension et les deux fichiers XML, cliquez sur **Envoyer vers**, puis cliquez sur **Dossier compressé**.  
  
8.  Renommez le fichier .zip que vous venez de créer *nom\_fichier*.vsix, où *nom\_fichier* correspond au nom du fichier redistribuable qui installe votre package.  
  
## Voir aussi  
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Élément PackageManifest \(élément racine, schéma VSX\)](http://msdn.microsoft.com/fr-fr/f8ae42ba-775a-4d2b-976a-f556e147f187)