---
title: "Vue d&#39;ensemble de l&#39;utilisation de fichiers de base de donn&#233;es locaux dans les solutions Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "données (développement Office dans Visual Studio), locaux"
  - "données locales (développement Office dans Visual Studio)"
  - "applications Office (développement Office dans Visual Studio), données"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Vue d&#39;ensemble de l&#39;utilisation de fichiers de base de donn&#233;es locaux dans les solutions Office
  Vous pouvez inclure une base de données, telle qu'un fichier SQL Server Express \(.mdf\) ou un fichier Microsoft Office Access \(.mdb\), dans votre solution Office.  Cela permet aux utilisateurs finaux de gérer une base de données locale lorsqu'il n'est pas nécessaire de disposer d'une base de données centralisée, par exemple dans une solution de stock locale utilisée sur un seul ordinateur.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Importation du fichier de base de données dans un projet  
 Pour importer le fichier de base de données dans votre projet, utilisez l'**Assistant Configuration de source de données** afin de créer une source de données reposant sur le fichier de base de données.  L'Assistant ajoute le fichier de base de données et un groupe de données typé à votre projet.  
  
## Déploiement du fichier de base de données  
 L' **Assistant Configuration de source de données** utilise un chemin d'accès relatif pour créer des connexions au fichier de base de données local.  Ceci vous permet de copier la solution d'un ordinateur à l'autre si vous maintenez les positions relatives des fichiers.  
  
 Si vous déployez votre solution sur un serveur et distribuez ensuite le document à chaque utilisateur final, vous devez également distribuer manuellement le fichier de base de données et l'installer à la même position relative dans le document.  Cela signifie que l'utilisateur final ne peut pas déplacer le document vers un nouvel emplacement sur son ordinateur, à moins qu'il ne déplace également le fichier de base de données.  
  
## Fichiers de base de données locaux et mise en cache du groupe de données  
 Dans les solutions au niveau du document pour Microsoft Office Excel et Microsoft Office Word, vous pouvez mettre en cache des groupes de données dans le document en marquant l'instance de groupe de données avec l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Lorsque vous ajoutez le fichier de base de données à votre projet à l'aide de l'**Assistant Configuration de source de données**, un groupe de données typé est automatiquement ajouté à votre projet.  Il est rarement nécessaire d'appliquer l'objet <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> à ce groupe de données car les données sont déjà locales sur l'ordinateur de l'utilisateur.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : remplir des documents avec les données d'une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Mise en cache des données](../vsto/caching-data.md)  
  
  