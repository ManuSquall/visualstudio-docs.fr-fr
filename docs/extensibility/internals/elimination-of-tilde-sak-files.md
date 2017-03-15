---
title: "&#201;limination de ~ SAK fichiers | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers temporaires"
  - "~ sak fichiers"
  - "source de plug-ins de contrôle, ~ les fichiers SAK"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# &#201;limination de ~ SAK fichiers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans l'API des plug\-ins 1,2 de contrôle de code source, les fichiers de ~SAK ont été remplacés par les balises de fonction et de nouvelles fonctions qui les détectent si un plug\-in contrôle de code source prend en charge le fichier de MSSCCPRJ et les extractions partagées.  
  
## fichiers de ~SAK  
 Visual Studio .NET 2003 a créé des fichiers temporaires pour préfixe le ~SAK.  Ces fichiers sont utilisés pour déterminer si un plug\-in contrôle de code source le prend en charge :  
  
-   le fichier de MSSCCPRJ.SCC.  
  
-   Plusieurs extractions \(partagés\).  
  
 Pour les connexions qui prennent en charge les fonctions avancées fournis dans l'API des plug\-ins 1,2 de contrôle de code source, l'IDE peuvent détecter ces fonctions sans créer les fichiers temporaires via l'utilisation de nouvelles fonctions, indicateur, et fonctions, détaillées dans les sections suivantes.  
  
## nouvelles balises de fonction  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## nouvelles fonctions  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un plug\-in contrôle de code source prend en charge plusieurs extractions \(partagés\), il déclare la fonction d' `SCC_CAP_MULTICHECKOUT` et implémente la fonction d' `SccIsMultiCheckOutEnabled` .  Cette fonction est appelée chaque fois qu'une opération d'extraction se produit sur les projets sous contrôle de code source de l'.  
  
 Si un plug\-in contrôle de code source prend en charge la création et utilisation d'un fichier de MSSCCPRJ.SCC, il déclare la fonction d' `SCC_CAP_SCCFILE` et implémente [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md).  Cette fonction est appelée avec une liste de fichiers.  La fonction retourne `TRUE/FALSE` pour chaque fichier indique si Visual Studio doit utiliser un fichier de MSSCCPRJ.SCC pour lui.  Si le plug\-in contrôle de code source décide de ne pas prendre en charge ces nouvelles fonctionnalités et fonctions, il peut utiliser la clé de Registre suivante pour désactiver la création de ces fichiers :  
  
 \[\=dword HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateTemporaryFilesInSourceControl " : 00000001  
  
> [!NOTE]
>  Si cette clé de Registre est définie sur un dword : 00000000\), il est toujours équivalente à la clé est inexistante, et tente de Visual Studio pour créer les fichiers temporaires.  Toutefois, si la clé de Registre est définie sur un dword : 00000001, Visual Studio n'essaie pas de créer des fichiers temporaires.  À la place il suppose que le plug\-in contrôle de code source ne prend pas en charge le fichier de MSSCCPRJ.SCC et ne prend pas en charge les extractions partagées.  
  
## Voir aussi  
 [Quelles sont les nouveautés dans la Source contrôle plug\-in API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)