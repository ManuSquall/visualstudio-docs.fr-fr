---
title: "COM Interop unregistration failed | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
Un problème s'est produit lors de la tentative d'annulation d'inscription d'une ancienne copie de l'assembly.  
  
 Si la propriété **Inscrire pour COM interop** est définie, le système de projet tente d'annuler en premier lieu l'inscription d'une ancienne copie de l'objet COM avant d'inscrire la copie qui vient d'être générée.  Cette opération est effectuée pour que le Registre soit à jour.  
  
 Consultez la page de propriétés **Générer** située dans le dossier Propriétés de configuration pour accéder à la propriété **Inscrire pour COM interop**.  
  
 Voici certaines des raisons possibles de l'échec :  
  
-   Incapacité d'annuler l'inscription de la bibliothèque de types précédente pour l'assembly.  Il peut s'agir d'un problème d'autorisations dans le Registre.  
  
-   Incapacité d'annuler l'inscription de l'ancien assembly.  Il peut également s'agir d'un problème d'autorisations dans le Registre.  
  
 Si le processus d'annulation d'inscription échoue, il peut se produire une fuite du GUID pour les objets CoCreatable, ainsi que pour n'importe quel GUID de bibliothèque de types.  Néanmoins, le processus de génération général réussit.  
  
## Voir aussi  
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)