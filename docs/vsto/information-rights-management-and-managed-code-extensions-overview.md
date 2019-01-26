---
title: Information rights management et vue d’ensemble des extensions de code managé
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbe61b1b9ca43b9c3e4e6d5bcdf82dd2b5e1438a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876042"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Information rights management et vue d’ensemble des extensions de code managé
  Microsoft Office Word et Microsoft Office Excel fournissent Information Rights Management (IRM), une fonctionnalité qui peut vous aider à empêcher des personnes non autorisées consultation ou modification des informations sensibles. Pour plus d’informations sur le fonctionnement de l’Information Rights Management, consultez l’aide de l’application Office spécifique.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Exécuter du code derrière des documents avec des autorisations restreintes  
 Si votre solution contient un document ou classeur qui utilise l’IRM, par défaut, Word et Excel ne permettent pas de code à exécuter. Si vous êtes l’auteur du document ou que vous avez accès en contrôle total, vous pouvez modifier la valeur par défaut afin que votre solution fonctionne. Pour plus d'informations, voir [Procédure : Autoriser le code de s’exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM empêche l’utilisation de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> pour récupérer ou manipuler des données mises en cache dans le document.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Utilisateurs finaux pour limiter les autorisations à des documents qui utilisent des extensions de code managé  
 Toute personne disposant d’un accès contrôle total au document ou au classeur dans votre solution peut utiliser IRM pour restreindre les autorisations. Par exemple, si un utilisateur final dans le service de comptabilité utilise une solution qui remplit automatiquement une feuille de calcul avec des données à partir d’une base de données, cet utilisateur peut souhaiter permettent de modifier l’accès uniquement aux utilisateurs de son propre service et un accès en lecture à d’autres personnes. Lorsque l’utilisateur ajoute des autorisations restreintes, par défaut, le code-behind de la feuille de calcul ne peut pas s’exécuter, et la feuille de calcul ne sera pas rempli avec les données.  
  
 Pour résoudre le problème, une personne disposant d’un accès contrôle total au document ou classeur doit modifier les paramètres d’autorisation par défaut pour autoriser l’accès par programmation au modèle objet. Pour plus d'informations, voir [Procédure : Autoriser le code de s’exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Protection de mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)  
