---
title: "COM Interop registration failed | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop registration failed
L'inscription d'un assembly qui expose une fonctionnalité aux clients COM a échoué.  Le processus de génération échoue si cette erreur se produit.  
  
 Les assemblys peuvent exposer des objets aux clients COM.  Le système de projet fournit une propriété permettant d'inscrire les classes exposées pour COM interop, ainsi que de générer et d'inscrire une bibliothèque de types, de sorte que ces classes puissent être utilisées par des langages de script et par Visual Basic 6.  
  
 Consultez la page de propriétés **Build** située dans le dossier **Propriétés de configuration** pour accéder à la propriété **Inscrire pour COM interop**.  
  
 Voici certaines des raisons possibles de l'échec :  
  
-   Incapacité de générer une bibliothèque de types pour l'assembly.  Il peut s'agir d'un problème d'espace disque ou d'un problème de verrouillage de fichier où la bibliothèque de types est verrouillée par Visual Studio ou un autre processus.  Il se peut par ailleurs que les bibliothèques de types pour les assemblys référencés ne soient pas correctement inscrites sur votre système.  
  
-   Incapacité d'inscrire la bibliothèque de types générée.  Il peut s'agir d'un problème d'autorisations dans le Registre.  
  
-   Incapacité d'inscrire les classes dans l'assembly.  Il peut s'agir d'un problème d'autorisations dans le Registre.  
  
 **Pour corriger cette erreur**  
  
-   Libérez de l'espace disque sur votre ordinateur.  
  
-   S'il y a un problème de verrouillage de fichier, redémarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Vérifiez que vous êtes connecté en tant qu'administrateur ou membre d'un groupe autorisé à accéder au Registre.  
  
## Voir aussi  
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)