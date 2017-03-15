---
title: "Mise en route (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fichiers .dbg"
  - "fichiers DBG"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Mise en route (Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'interface Access \(DIA\) Kit de développement logiciel de débogage vous donne à la documentation d'instruction et un exemple qui indique comment utiliser l'API de diamètre.  Utilisez les interfaces et les méthodes du diamètre Kit de développement logiciel pour développer des applications personnalisées qui ouvrent les fichiers .pdb et de .dbg et trouvent leur contenu pour les symboles, des valeurs, des attributs, des adresses, et d'autres informations de débogage.  Ce Kit de développement logiciel fournit également des tables de référence pour les propriétés associées aux symboles présents dans les applications C\+\+.  
  
 Une meilleure utilisation diamètre le Kit de développement, vous devez être familiarisé avec les éléments suivants :  
  
-   langage de programmation C\+\+  
  
-   Programmation COM  
  
-   Environnement de développement intégré Visual \(IDE\) Studio pour compiler les exemples  
  
 Le diamètre Kit de développement logiciel est normalement installé avec Visual Studio et son emplacement par défaut est *\[lecteur\]*\\Program Files\\Microsoft Visual Studio 9.0\\DIA SDK.  Dans le cadre de l'installation, le msdia90.dll, qui implémente le diamètre Kit de développement, est enregistré automatiquement ce que vous devez faire pour utiliser qu'il doit inclure `dia2.h` dans votre programme et lien vers `diaguids.lib`.  
  
 en\-tête : include \\ dia2.h  
  
 bibliothèque : lib \\ diaguids.lib  
  
 DLL : bin \\ msdia80.dll  
  
 IDL : IDL \(interface definition langage\) \\ dia2.idl  
  
## Dans cette section  
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 examine l'architecture de base du diamètre.  
  
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fournit des instructions pas \- à \- pas sur la façon d'utiliser l'API de diamètre d'interroger un fichier .pdb.  
  
## Voir aussi  
 [Kit de développement logiciel de Debug Interface Access](../../debugger/debug-interface-access/debug-interface-access-sdk.md)