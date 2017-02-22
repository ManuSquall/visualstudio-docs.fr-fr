---
title: "How to: Include a Data File in a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, data"
  - "deploying applications [ClickOnce], data files"
  - "data access, ClickOnce applications"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Include a Data File in a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un répertoire de données sur le disque local de l'ordinateur de destination est assigné à chaque application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que vous installez où l'application peut gérer ses propres données.  Les fichiers de données peuvent être de tout type : des fichiers texte, des fichiers XML, voire des fichiers de base de données Microsoft Access \(.mdb\).  Les procédures suivantes montrent comment ajouter un fichier de données d'un type quelconque à votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Pour inclure un fichier de données avec Mage.exe  
  
1.  Ajoutez le fichier de données à votre répertoire de l'application avec le reste des fichiers de votre application.  
  
     En général, votre répertoire de l'application est un répertoire indiquant la version actuelle du déploiement, par exemple v1.0.0.0.  
  
2.  Mettez à jour le manifeste d'application pour répertorier le fichier de données.  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     Effectuer cette tâche recrée la liste des fichiers dans votre manifeste d'application et génère automatiquement les signatures de hachage.  
  
3.  Ouvrez le manifeste d'application dans votre éditeur XML ou éditeur de texte par défaut et recherchez l'élément `file` du fichier récemment ajouté.  
  
     Si vous avez ajouté un fichier XML nommé `Data.xml`, le fichier ressemblera à l'exemple de code suivant.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Ajoutez l'attribut `type` à cet élément et spécifiez pour celui\-ci une valeur `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Resignez votre manifeste d'application à l'aide de votre paire de clés ou de votre certificat, puis resignez votre manifeste de déploiement.  
  
     Vous devez resigner votre manifeste de déploiement parce que son hachage a changé.  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### Pour inclure un fichier de données avec MageUI.exe  
  
1.  Ajoutez le fichier de données à votre répertoire de l'application avec le reste des fichiers de votre application.  
  
2.  En général, votre répertoire de l'application est un répertoire indiquant la version actuelle du déploiement, par exemple v1.0.0.0.  
  
3.  Dans le menu **File**, cliquez sur **Open** pour ouvrir votre manifeste d'application.  
  
4.  Sélectionnez l'onglet **Files**.  
  
5.  Dans la zone de texte en haut de l'onglet, entrez le répertoire qui contient les fichiers de votre application, puis cliquez sur **Populate**.  
  
     Votre fichier de données apparaîtra dans la grille.  
  
6.  Attribuez **Data** à la valeur **File Type** du fichier de données.  
  
7.  Enregistrez le manifeste d'application, puis resignez le fichier.  
  
     MageUI.exe vous invite ensuite à resigner le fichier.  
  
8.  Resigner votre manifeste de déploiement  
  
     Vous devez resigner votre manifeste de déploiement parce que son hachage a changé.  
  
## Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)