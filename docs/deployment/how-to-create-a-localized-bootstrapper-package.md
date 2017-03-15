---
title: "Comment&#160;: cr&#233;er un package du programme d&#39;amor&#231;age localis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dépendances, créer des packages du programme d'amorçage localisé"
  - "packages du programme d'amorçage localisé"
  - "composants requis, créer des packages du programme d'amorçage localisé"
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er un package du programme d&#39;amor&#231;age localis&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Après avoir créé un package de programme d'amorçage, vous pouvez créer des versions localisées de ce dernier en créant deux fichiers de plus pour chacun des paramètres régionaux : un fichier des termes du contrat de licence logiciel \(par exemple eula.rtf\) et un manifeste du package \(package.xml\).  
  
 Par défaut, Visual Studio 2010 inclut des packages de programme d'amorçage localisés uniquement pour .NET Framework 4, .NET Framework 4 Client Profile, F\# Runtime 2.0 et F\# Runtime 4.0.  Vous pouvez créer des packages localisés pour d'autres programmes d'amorçage en trois étapes.  
  
1.  Créez un dossier nommé en fonction du nom des paramètres régionaux dans \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages\\*nom\_package\_programme\_amorçage*.  
  
2.  Créez un fichier qui contient les termes du contrat de licence logiciel du package du programme d'amorçage et placez\-le dans le nouveau dossier.  
  
3.  Créez un manifeste du package nommé package.xml, mettez à jour les chaînes et la culture, puis placez le fichier dans le nouveau dossier.  Si vous avez déjà créé un programme d'amorçage de Visual Studio dans la langue cible, vous pouvez copier le fichier Visual Studio package.xml et le changer durant cette étape.  
  
> [!NOTE]
>  Si vous utilisez un projet d'installation pour déployer les applications, vous pouvez localiser votre application en changeant la propriété **Localization**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour créer un package de programme d'amorçage localisé  
  
1.  Créez un dossier nommé en fonction du nom des paramètres régionaux.  
  
     Sur les ordinateurs 32 bits, créez le dossier dans le dossier \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages\\*nom\_package\_programme\_amorçage*\\.  
  
     Sur les ordinateurs 64 bits, créez le dossier dans le dossier \\Program Files \(86\)\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages\\*nom\_package\_programme\_amorçage*\\.  
  
     Le tableau suivant indique les noms de dossiers qui peuvent correspondre à des paramètres régionaux.  
  
    |Paramètres régionaux|Nom de dossier|  
    |--------------------------|--------------------|  
    |Chinois \(simplifié\)|zh\-Hans|  
    |Chinois \(traditionnel\)|zh\-Hant|  
    |Tchèque|cs|  
    |Allemand|de|  
    |Anglais|en|  
    |Espagnol|es|  
    |Français|fr|  
    |Italien|it|  
    |Coréen|ko|  
    |Japonais|ja|  
    |Polonais|pl|  
    |Portugais \(Brésil\)|pt\-BR|  
    |Russe|ru|  
    |Turc|tr|  
  
2.  Créez un fichier qui contient les termes du contrat de licence logiciel du package du programme d'amorçage et placez\-le dans le nouveau dossier.  
  
3.  Créez un manifeste du package nommé package.xml et placez\-le dans le nouveau dossier.  Pour plus d'informations, consultez [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Mettez à jour la section `<Strings>` du manifeste du package pour que les chaînes soient dans la langue appropriée en fonction des paramètres régionaux.  
  
5.  Changez la valeur de `<String Name="Culture">` pour qu'elle corresponde au nom du dossier.  
  
6.  Enregistrez le fichier package.xml.  
  
### Pour créer un package de programme d'amorçage pour .NET Framework 3.5 Service Pack 1 localisé en français  
  
1.  Créez un dossier nommé fr.  Le nom du dossier doit correspondre au nom des paramètres régionaux.  
  
     Sur les ordinateurs 32 bits, créez le dossier dans le dossier \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages\\DotNetFX35SP1\\.  
  
     Sur les ordinateurs 64 bits, créez le dossier dans le dossier \\Program Files \(86\)\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages\\DotNetFX35SP1\\.  
  
2.  Placez une version localisée des termes du contrat de licence logiciel dans le dossier fr.  
  
3.  Copiez le fichier \\Program Files \(x86\)\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages\\DotNetFX35SP1\\en\\package.xml dans le dossier fr, puis ouvrez le fichier dans le Concepteur XML.  
  
4.  Mettez à jour la section `<Strings>` du manifeste du package pour que les chaînes d'erreur soient en français.  
  
5.  Changez la valeur de `<String Name="Culture">` en fr.  
  
6.  Enregistrez le fichier package.xml.  
  
## Voir aussi  
 [Création de packages de programme d'amorçage](../deployment/creating-bootstrapper-packages.md)   
 [Composants requis pour le déploiement d'applications](../deployment/application-deployment-prerequisites.md)   
 [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md)