---
title: Information rights management et vue d’ensemble des extensions de code managé
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Information rights management et vue d’ensemble des extensions de code managé
  Microsoft Office Word et Microsoft Office Excel fournissent Information Rights Management (IRM), une fonctionnalité qui peut vous aider à empêcher les personnes non autorisées d’affichage ou la modification d’informations sensibles. Pour plus d’informations sur le fonctionnement de l’Information Rights Management, consultez l’aide de l’application Office spécifique.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Exécuter le code derrière des documents avec des autorisations restreintes  
 Si votre solution contient un document ou classeur qui utilise l’IRM, par défaut, Word et Excel ne permettent pas de code à exécuter. Si vous êtes l’auteur du document ou que vous avez accès en contrôle total, vous pouvez modifier la valeur par défaut afin que votre solution fonctionne. Pour plus d’informations, consultez [Comment : permettre au code à exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM empêche l’utilisation de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> pour récupérer ou manipuler des données mises en cache dans le document.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Utilisateurs finaux pour limiter les autorisations à des documents qui utilisent des extensions de code managé  
 Toute personne qui dispose d’un accès contrôle total au document ou au classeur dans votre solution peut utiliser IRM pour limiter les autorisations. Par exemple, si un utilisateur final du service comptabilité utilise une solution qui remplit automatiquement une feuille de calcul avec des données à partir d’une base de données, cet utilisateur peut vouloir autoriser modifier l’accès uniquement aux utilisateurs de son propre service et l’accès en lecture à d’autres personnes. Lorsque l’utilisateur ajoute les autorisations restreintes, par défaut, le code-behind de la feuille de calcul ne peut pas s’exécuter, et la feuille de calcul n’est pas peuplée avec des données.  
  
 Pour résoudre le problème, une personne disposant de l’accès contrôle total au document ou au classeur doit modifier les paramètres d’autorisation par défaut pour autoriser l’accès par programme au modèle objet. Pour plus d’informations, consultez [Comment : permettre au code à exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Mot de passe sur des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  