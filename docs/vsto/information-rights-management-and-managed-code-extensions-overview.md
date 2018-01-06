---
title: "Vue d’ensemble des Extensions de Code managé et de gestion des droits | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 21431cd16407d61db6f981aad68d52906c2de1f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Vue d’ensemble de la gestion des droits relatifs à l’information et des extensions de code managé
  Microsoft Office Word et Microsoft Office Excel fournissent Information Rights Management (IRM), une fonctionnalité qui peut vous aider à empêcher les personnes non autorisées d’affichage ou la modification d’informations sensibles. Pour plus d’informations sur le fonctionnement de l’Information Rights Management, consultez l’aide de l’application Office spécifique.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Exécution du Code derrière des Documents avec des autorisations restreintes  
 Si votre solution contient un document ou classeur qui utilise l’IRM, par défaut, Word et Excel ne permettent pas de code à exécuter. Si vous êtes l’auteur du document ou que vous avez accès en contrôle total, vous pouvez modifier la valeur par défaut afin que votre solution fonctionne. Pour plus d’informations, consultez [Comment : autoriser le Code à exécuter derrière des Documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM empêche l’utilisation de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> pour récupérer ou manipuler des données mises en cache dans le document.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Utilisateurs finaux en limitant les autorisations à des Documents qui utilisent des Extensions de Code managé  
 Toute personne qui dispose d’un accès contrôle total au document ou au classeur dans votre solution peut utiliser IRM pour limiter les autorisations. Par exemple, si un utilisateur final du service comptabilité utilise une solution qui remplit automatiquement une feuille de calcul avec des données à partir d’une base de données, cet utilisateur peut vouloir autoriser modifier l’accès uniquement aux utilisateurs de son propre service et l’accès en lecture à d’autres personnes. Lorsque l’utilisateur ajoute les autorisations restreintes, par défaut, le code-behind de la feuille de calcul ne peut pas s’exécuter, et la feuille de calcul n’est pas peuplée avec des données.  
  
 Pour résoudre le problème, une personne disposant de l’accès contrôle total au document ou au classeur doit modifier les paramètres d’autorisation par défaut pour autoriser l’accès par programme au modèle objet. Pour plus d’informations, consultez [Comment : autoriser le Code à exécuter derrière des Documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Protection des documents dans les Solutions au niveau du Document](../vsto/document-protection-in-document-level-solutions.md)   
 [Mot de passe sur des Documents Office](../vsto/password-protection-on-office-documents.md)   
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  