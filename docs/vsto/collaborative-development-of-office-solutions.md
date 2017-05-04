---
title: "D&#233;veloppement collaboratif de solutions Office | Microsoft Docs"
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
  - "développement collaboratif (développement Office dans Visual Studio)"
  - "applications Office (développement Office dans Visual Studio), développement collaboratif"
  - "développement Office dans Visual Studio, collaboration"
  - "contrôle de code source (développement Office dans Visual Studio)"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# D&#233;veloppement collaboratif de solutions Office
  Plusieurs développeurs peuvent travailler sur un même projet Office de la même façon qu'ils collaborent sur d'autres projets Visual Studio.  Visual Studio localise correctement l'installation Microsoft Office sur chaque ordinateur, même si Office est installé dans des emplacements différents.  Toutefois, certaines considérations importantes doivent être prises en compte.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Les propriétés de débogage ne sont pas partagées  
 Les propriétés de débogage ne sont pas partagées entre plusieurs utilisateurs sous contrôle de code source.  Les projets Visual Basic et C\# stockent les propriétés de débogage dans un fichier propre à l'utilisateur \(*NomProjet*.vbproj.user ou *NomProjet*.csproj.user\), qui n'est pas sous contrôle de code source.  Si plusieurs personnes effectuent un débogage, chacune d'entre elles doit entrer manuellement les propriétés de débogage.  
  
 Si le projet est hébergé sur un partage réseau au lieu d'un contrôle de code source, certaines étapes supplémentaires doivent être prises pour permettre aux développeurs travaillant en collaboration d'ouvrir la solution et de tester l'assembly.  
  
## Le contrôle de code source requiert l'extraction de tous les fichiers  
 Si vous utilisez le contrôle de code source pour vos projets, vous devez extraire tous les fichiers sous un fichier de code dans l'**Explorateur de solutions** \(tel que les fichiers de code ThisDocument, ThisWorkbook ou ThisAddIn\) chaque fois que vous modifiez le fichier de code, y compris les fichiers masqués par défaut.  Si vous extrayez uniquement le fichier de code de niveau supérieur, vous risquez de perdre les modifications apportées.  
  
 Une fois les changements effectués, archivez tous les fichiers.  Pour plus d'informations sur le code masqué des projets, consultez [Projets Office dans l'environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Sécurité pour une collaboration informelle sur un réseau  
 Pour toutes les solutions au niveau du document qui sont dans un emplacement réseau \(tel que \\\\*NomServeur*\\*NomPartage*\), l'emplacement qualifié complet doit être ajouté à la liste des dossiers approuvée dans l'application Microsoft Office avec laquelle vous travaillez.  Sélectionnez l'option permettant d'inclure les sous\-répertoires sous le dossier principal ou ajoutez spécifiquement des dossiers de débogage et de génération à la liste approuvée des dossiers.  Pour plus d'informations sur la manière de procéder, consultez [Octroi de niveaux de confiance à des documents](../vsto/granting-trust-to-documents.md).  
  
 Les certificats temporaires créés automatiquement au moment de la génération ne sont pas sécurisés par mots de passe.  Les certificats contiennent le nom de connexion du développeur et d'autres informations personnelles.  Si vous déployez des personnalisations signées par des certificats temporaires, des tiers risquent d'avoir accès à ces informations.  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)  
  
  