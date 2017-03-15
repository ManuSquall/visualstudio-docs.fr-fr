---
title: "Valeurs par d&#233;faut VB, Projets, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Option Explicit (instruction), définition dans l’IDE"
  - "Option Compare (instruction), définition dans l’IDE"
  - "Option Strict (instruction), définition dans l’IDE"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Valeurs par d&#233;faut VB, Projets, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie les paramètres par défaut pour les options de projet Visual Basic.  Lorsqu'un projet est créé, les instructions d'options spécifiées sont ajoutées à l'en\-tête du projet dans l'éditeur de code.  Ces options s'appliquent à tous les projets Visual Basic.  
  
 Pour accéder à cette boîte de dialogue, dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Projets et solutions** et cliquez sur **Valeurs par défaut VB**.  
  
 **Option Explicit**  
 Configure le compilateur de manière à ce qu'une déclaration explicite des variables soit requise par défaut.  Par défaut, **Option Explicit** a la valeur **On**.  Pour plus d'informations, consultez [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Configure le compilateur de manière à ce qu'une conversion restrictive explicite soit requise et que les liaisons tardives soient interdites.  Par défaut, **Option Strict** a la valeur **Off**.  Pour plus d'informations, consultez [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Configure la méthode de comparaison de chaînes à utiliser par le compilateur: Binary \(respect de la casse\) ou Text \(non\-respect de la casse\). Par défaut, **Option Compare** a la valeur **Binary**.  Pour plus d'informations, consultez [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Définit la valeur par défaut du compilateur pour une inférence de type local.  Par défaut, **Option Infer** a la valeur **On** pour les projets récemment créés et la valeur **Off** pour les projets migrés créés dans les versions antérieures de Visual Basic.  Pour plus d'informations, consultez [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## Voir aussi  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)