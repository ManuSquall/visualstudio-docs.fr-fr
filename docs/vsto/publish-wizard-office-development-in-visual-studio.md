---
title: "Assistant Publication (D&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "déploiement ClickOnce (développement Office dans Visual Studio), Assistant Publication"
  - "déploiement d’applications (développement Office dans Visual Studio), Assistant Publication"
  - "applications Office (développement Office dans Visual Studio), Assistant Publication"
  - "Assistant Publication, solutions Office"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Assistant Publication (D&#233;veloppement Office dans Visual Studio)
  Utilisez **Assistant Publication** pour copier les fichiers solution vers un emplacement spécifié, créez des fichiers manifeste, et créer un programme d'installation.  
  
 Pour accéder à cet Assistant, dans le menu de **Générer** , choisissez **Publier** *SolutionName*.  Vous pouvez également accéder à l'**Assistant Publication** à partir de l'**Explorateur de solutions**.  Ouvrez le menu contextuel du nœud de projet, puis choisissez **Publier**.  
  
 Chacune des sections suivantes décrit une page de l'Assistant.  
  
## Où souhaitez\-vous publier l'application ?  
 **Spécifiez l'emplacement de publication de cette application**  
 Obligatoire.  L'emplacement de publication est le répertoire où l'**Assistant Publication** copie les fichiers de la solution, tels que les manifestes, les assemblys, le certificat temporaire et les autres fichiers de la génération.  Vous devez avoir accès en écriture à ce répertoire.  
  
 Tapez l'emplacement sous la forme d'un chemin d'accès au disque, partage de fichiers, un site FTP, ou URL de site Web, ou cliquez sur le bouton de **Parcourir** pour rechercher l'emplacement.  Le chemin d'accès peut être dans ces formats :  
  
-   Un chemin d'accès relatif ou absolu, au format Windows standard, par exemple : C:\\Deploy\\MyApplication ou \\MyApplication.  
  
-   Un chemin d'accès UNC \(Universal Naming Convention\), tel que \\\\NomServeur\\MyApplication\\.  
  
-   UNE URL d'un site Web, par exemple http:\/\/www.microsoft.com\/MyApplication.  
  
 L'emplacement de publication par défaut est *http:\/\/localhost\/NomProjet\/* si vous avez installé IIS, ou le répertoire publish\\ si IIS n'est pas installé.  
  
> [!NOTE]  
>  D'autres aspects doivent être pris en compte si l'ordinateur cible fonctionne sous Windows Vista.  Pour utiliser l'option de publication locale, vous devez être administrateur sur l'ordinateur Windows Vista.  De plus, l'emplacement par défaut est toujours le répertoire *publish\\*, qu'IIS soit installé ou non.  
  
## Quel est le chemin d'installation par défaut sur les ordinateurs des utilisateurs finaux ?  
 Le chemin d'installation est facultatif.  Vous pouvez définir le chemin d'installation ultérieurement si vous préférez.  Pour plus d'informations, consultez [Comment : modifier le chemin d'installation d'une solution Office](http://msdn.microsoft.com/fr-fr/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Le chemin d'installation est le répertoire à partir duquel l'utilisateur final installera la personnalisation.  C'est également le chemin qu'utilisera la solution pour rechercher des mises à jour.  L'**Assistant Publication** ne déploie pas la solution à cet emplacement, à moins que le chemin d'accès soit le même que celui spécifié dans la zone **Spécifiez l'emplacement de publication de cette application** sur la page précédente.  
  
 **À partir d'un site Web**  
 Spécifiez l'URL que les utilisateurs finaux suivront pour installer la solution.  
  
 **À partir d'un chemin UNC ou d'un partage de fichiers**  
 Spécifiez le chemin UNC que les utilisateurs finaux suivront pour installer la solution.  
  
 **À partir d'un CD\-ROM ou d'un DVD\-ROM**  
 Cette option ne requiert pas de chemin d'installation.  
  
 Visual Studio ne grave pas le CD ou DVD.  Vous devez copier manuellement la sortie vers un CD ou DVD.  
  
## Voir aussi  
 [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Page Publier, Concepteur de projets &#40;Développement Office dans Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)  
  
  