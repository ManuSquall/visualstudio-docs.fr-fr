---
title: "Param&#232;tres du projet VC++, Projets et solutions, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VCBuild"
helpviewer_keywords: 
  - "builds [Visual Studio], journaux"
  - "processus de génération (C++)"
  - "fichiers [Visual Studio], générés par le compilateur C/C++"
  - "extensions de fichier, générées par le compilateur C ou C++"
  - "compilateur cl.exe, extensions de fichier"
  - "extensions, fichiers générées par le compilateur C ou C++"
  - "BuildLog.htm"
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Param&#232;tres du projet VC++, Projets et solutions, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de définir les paramètres du projet [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] relatifs au journal de génération et à la prise en charge des types de fichiers.  
  
### Pour accéder à cette boîte de dialogue  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Sélectionnez **Projets et solutions**, puis sélectionnez **Paramètres de projet VC\+\+**.  
  
## Chemin de recherche des personnalisations de la build  
 Spécifie la liste des répertoires qui contiennent les fichiers .rules, qui vous aident à définir des règles de génération pour vos projets.  
  
## Journalisation de la génération  
 **Oui**  
 Active la création du fichier journal de génération.  Cette option génère le fichier BuildLog.htm, qui se trouve dans le répertoire des fichiers intermédiaires du projet.  Chaque nouvelle génération écrase le fichier BuildLog.htm précédent.  
  
 **Non**  
 Désactive la création du fichier journal de génération.  
  
## Minutage de la génération  
 **Oui**  
 Active le minutage de la génération.  Si vous sélectionnez cette option, la durée de la génération est enregistrée dans la fenêtre Sortie.  Pour plus d'informations, consultez [Fenêtre Sortie](../../ide/reference/output-window.md).  
  
 **Non**  
 Désactive le minutage de la génération.  
  
## Extensions à masquer  
 Spécifie les extensions de noms de fichiers qui ne s'affichent pas dans l'**Explorateur de solutions** lorsque l'option **Afficher tous les fichiers** est activée.  
  
## Extensions à inclure  
 Spécifie les extensions de noms de fichiers des fichiers qui peuvent être portés dans votre projet.  
  
## Nombre maximal de compilations C\+\+ simultanées  
 Spécifie le nombre maximal de cœurs d'UC à utiliser pour la compilation parallèle C\+\+.  
  
## Affichage de l'environnement dans le journal  
 **Oui**  
 Répertorie les variables d'environnement dans le fichier journal de génération.  Cette option indique de répercuter toutes les variables d'environnement, au cours de la génération des projets [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)], dans le fichier journal de génération.  
  
 **Non**  
 Excluez les variables d'environnement du fichier journal de génération.  
  
## Mode Explorateur de solutions  
 **Afficher uniquement les fichiers du projet**  
 Configure l'**Explorateur de solutions** de sorte qu'il n'affiche que les fichiers du projet.  
  
 **Afficher tous les fichiers**  
 Configure l'**Explorateur de solutions** de sorte qu'il affiche les fichiers du projet et les fichiers sur disque dans le dossier du projet.  
  
## Voir aussi  
 [Génération de programmes C\/C\+\+](/visual-cpp/build/building-c-cpp-programs)   
 [Référence à la génération C\/C\+\+](/visual-cpp/build/reference/c-cpp-building-reference)