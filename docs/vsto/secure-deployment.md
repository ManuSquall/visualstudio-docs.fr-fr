---
title: "D&#233;ploiement s&#233;curis&#233; | Microsoft Docs"
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
  - "déploiement ClickOnce (développement Office dans Visual Studio), sécurité"
  - "déployer des applications (développement Office dans Visual Studio), sécurité"
  - "applications Office (développement Office dans Visual Studio), sécurité"
  - "développement Office dans Visual Studio, sécurité"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# D&#233;ploiement s&#233;curis&#233;
  Lorsque vous créez une solution Office, votre ordinateur de développement est mis à jour automatiquement pour autoriser l'exécution du code dans votre projet.  Toutefois, lorsque vous déployez votre solution, vous devez fournir une preuve sur laquelle la décision d'approbation sera basée en signant la solution avec un certificat ou en utilisant la clé d'invite d'approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Pour plus d’informations, consultez [Octroi de niveaux de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Pour les personnalisations au niveau du document, si vous déployez le document sur un emplacement réseau, vous devez également ajouter l'emplacement du document à la liste des emplacements approuvés du Centre de gestion de la confidentialité de l'application Office.  Pour plus d'informations sur la définition des autorisations relatives aux documents sur les ordinateurs des utilisateurs finaux, consultez [Octroi de niveaux de confiance à des documents](../vsto/granting-trust-to-documents.md).  
  
## Empêcher les solutions Office d'exécuter du code  
 Les administrateurs peuvent utiliser le Registre pour empêcher toutes les solutions Office d'exécuter du code sur un ordinateur.  Lorsqu'une solution Office qui a des extensions de code managé est ouverte, le runtime de Visual Studio Tools pour Office vérifie si une entrée avec le nom `Disabled` existe sous l'une des clés de Registre suivantes sur l'ordinateur :  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Pour empêcher les solutions Office de niveau document d'exécuter du code, créez une entrée `Disabled` sous l'une de ces clés de Registre, ou sous les deux, et spécifiez un type de données ainsi qu'une valeur pour `Disabled` parmi les choix suivants :  
  
-   REG\_SZ ou REG\_EXPAND\_SZ dont la valeur correspond à toute chaîne autre que "0" \(zéro\).  
  
-   REG\_DWORD dont la valeur est différente de 0 \(zéro\).  
  
 Pour permettre aux solutions Office de niveau document d'exécuter du code, affectez la valeur 0 \(zéro\) à chacune des entrées `Disabled` ou bien supprimez les entrées du Registre.  
  
## Voir aussi  
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Préparation d'ordinateurs pour exécuter ou héberger des solutions Office](http://msdn.microsoft.com/fr-fr/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)  
  
  