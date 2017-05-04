---
title: "Octroi de niveaux de confiance &#224; des documents | Microsoft Docs"
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
  - "accorder des niveaux de confiance (développement Office dans Visual Studio)"
  - "listes d'inclusion (développement Office dans Visual Studio), à propos des listes d'inclusion"
  - "sécurité (développement Office dans Visual Studio), confiance"
  - "confiance (développement Office dans Visual Studio), Office System 2007"
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Octroi de niveaux de confiance &#224; des documents
  Un projet au niveau du document présente les mêmes exigences de sécurité que les projets au niveau de l'application : il convient de signer les manifestes à l'aide d'un certificat ou de cliquer sur l'invite d'approbation.  En outre, le document ou le classeur doit se trouver dans un répertoire désigné comme emplacement approuvé.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Emplacements approuvés  
 Les applications inscrites dans [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et Office 2010 disposent de centres de gestion de la confidentialité dans lesquels les utilisateurs peuvent configurer des paramètres de sécurité et de confidentialité, tels que des emplacements approuvés.  Pour les solutions Office, l'ordinateur local est considéré comme un emplacement approuvé. Toutefois, en raison de risques plus élevés, certains répertoires ne peuvent jamais être approuvés, tels que les dossiers temporaires système propres à chaque utilisateur et à Internet Explorer.  
  
 Pour plus d'informations sur les centres de gestion de la confidentialité, consultez [Stratégies et paramètres de sécurité dans Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202).  Pour plus d'informations sur la façon de créer, gérer, supprimer et configurer des dossiers approuvés, consultez [Configurer les paramètres des éditeurs approuvés et des emplacements approuvés dans Office System 2007](http://go.microsoft.com/fwlink/?LinkId=89203) et [Créer, supprimer ou modifier un emplacement approuvé pour vos fichiers](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## Considérations spécifiques à la sécurité pour les solutions Office  
 Plusieurs problèmes de sécurité se posent quand vous déterminez les dossiers à ajouter aux emplacements approuvés :  
  
-   Les dossiers locaux sont considérés plus sécurisés et ils sont approuvés de manière implicite.  Les emplacements distants tels que les partages de fichiers doivent être désignés comme emplacements approuvés.  
  
-   Quand vous ajoutez un répertoire aux emplacements approuvés, vous accordez une confiance totale aux solutions Office, mais également au code VBA et ActiveX.  Par conséquent, le répertoire racine et le dossier Mes documents ne doivent pas être désignés comme approuvés.  
  
-   Le document lui\-même est approuvé en utilisant les emplacements approuvés. Toutefois, des autorisations supplémentaires sont requises pour approuver la personnalisation.  Vous pouvez accorder une confiance totale à la personnalisation en signant les manifestes avec un certificat, en cliquant sur l'invite d'approbation ou en installant la solution Office dans le répertoire Program Files.  
  
-   Vous pouvez stocker le document ou le classeur d'une solution au niveau du document dans le même répertoire que l'assembly ou dans un répertoire différent.  Par exemple, le document peut être situé sur un serveur SharePoint et l'assembly dans un partage de fichiers réseau.  Pour plus d'informations, consultez [Comment : publier une solution Office au niveau d'un document vers un serveur SharePoint à l'aide de ClickOnce](http://msdn.microsoft.com/fr-fr/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## Voir aussi  
 [Octroi de niveaux de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Dépannage de la sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)  
  
  