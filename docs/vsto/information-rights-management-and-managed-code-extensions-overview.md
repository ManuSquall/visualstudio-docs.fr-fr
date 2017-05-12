---
title: "Vue d&#39;ensemble de la gestion des droits relatifs &#224; l&#39;information et des extensions de code manag&#233;"
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
  - "documents (développement Office dans Visual Studio), autorisations restreintes"
  - "Gestion des droits relatifs à l'information (développement Office dans Visual Studio)"
  - "IRM (développement Office dans Visual Studio)"
  - "documents Office (développement Office dans Visual Studio), autorisations restreintes"
  - "gestion des droits (développement Office dans Visual Studio)"
  - "classeurs (développement Office dans Visual Studio), autorisations restreintes"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Vue d&#39;ensemble de la gestion des droits relatifs &#224; l&#39;information et des extensions de code manag&#233;
  Microsoft Office Word et Microsoft Office Excel fournissent une fonctionnalité, l'Information Rights Management \(IRM\), qui vous permet d'empêcher la consultation ou la modification d'informations sensibles par des personnes non autorisées.  Pour plus d'informations sur le fonctionnement de la fonctionnalité Information Rights Management, consultez l'aide de l'application Office concernée.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Exécution du code pour des documents dotés d'autorisations restreintes  
 Si votre solution contient un document ou un classeur qui utilise la fonctionnalité IRM, par défaut, Word et Excel bloquent toute exécution de code.  Si vous êtes l'auteur du document ou si vous disposez d'un accès avec contrôle total, vous pouvez modifier la valeur par défaut de sorte que votre solution puisse fonctionner.  Pour plus d’informations, consultez [Comment : permettre au code de s'exécuter derrière des documents dotés d'autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 La fonctionnalité IRM empêche l'utilisation de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> pour récupérer ou manipuler des données mises en cache dans le document.  
  
## Restriction des autorisations par les utilisateurs finaux sur les documents qui utilisent des extensions de code managé  
 Toute personne qui dispose d'un accès avec contrôle total au document ou classeur de votre solution peut utiliser la fonctionnalité IRM pour restreindre les autorisations.  Par exemple, un utilisateur final du service comptable utilise une solution qui remplit automatiquement une feuille de calcul à l'aide des données d'une base de données ; cet utilisateur peut autoriser l'accès en écriture uniquement aux personnes de son service et l'accès en lecture aux autres personnes.  Lorsque l'utilisateur ajoute les autorisations restreintes, par défaut, l'exécution du code\-behind de la feuille de calcul est bloquée. Par conséquent, aucune donnée n'est ajoutée à la feuille de calcul.  
  
 Pour résoudre le problème, une personne qui dispose d'un accès avec contrôle total au document ou classeur doit modifier les paramètres d'autorisation par défaut, afin de permettre un accès par programmation au modèle objet.  Pour plus d’informations, consultez [Comment : permettre au code de s'exécuter derrière des documents dotés d'autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Protection par mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  