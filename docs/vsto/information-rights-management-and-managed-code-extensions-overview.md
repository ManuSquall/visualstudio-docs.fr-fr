---
title: Gestion des droits relatifs à l’information & extensions de code managé
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
ms.openlocfilehash: 753f3d2da201c67cd86c697eccf7580596a40d6e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872065"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Présentation de la gestion des droits relatifs à l’information et des extensions de code managé
  Microsoft Office Word et Microsoft Office Excel fournissent des informations Rights Management (IRM), une fonctionnalité qui peut vous aider à empêcher des personnes non autorisées d’afficher ou de modifier des informations sensibles. Pour plus d’informations sur le fonctionnement de l’Rights Management d’informations, consultez l’aide dans l’application Office spécifique.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Exécuter du code derrière des documents avec des autorisations restreintes
 Si votre solution contient un document ou un classeur qui utilise IRM, par défaut, Word et Excel n’autorisent pas l’exécution de code. Si vous êtes l’auteur du document ou que vous disposez d’un accès contrôle total, vous pouvez modifier la valeur par défaut afin que votre solution fonctionne. Pour plus d’informations, consultez [Guide pratique pour Autoriser le code à s’exécuter derrière des documents](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)avec des autorisations restreintes.

 IRM empêche l’utilisation <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> de pour extraire ou manipuler les données mises en cache dans le document.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Utilisateurs finaux pour limiter les autorisations aux documents qui utilisent des extensions de code managé
 Toute personne disposant d’un accès de contrôle total au document ou au classeur dans votre solution peut utiliser IRM pour restreindre les autorisations. Par exemple, si un utilisateur final dans le service comptabilité utilise une solution qui remplit automatiquement une feuille de calcul avec des données provenant d’une base de données, il peut souhaiter autoriser l’accès en modification uniquement aux personnes de son service et à l’accès en lecture aux autres utilisateurs. Lorsque l’utilisateur ajoute les autorisations restreintes, par défaut, le code derrière la feuille de calcul ne peut pas s’exécuter et la feuille de calcul n’est pas remplie de données.

 Pour résoudre le problème, une personne disposant d’un accès contrôle total au document ou au classeur doit modifier les paramètres d’autorisation par défaut pour autoriser l’accès par programme au modèle objet. Pour plus d’informations, consultez [Guide pratique pour Autoriser le code à s’exécuter derrière des documents](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)avec des autorisations restreintes.

## <a name="see-also"></a>Voir aussi
- [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)
- [Protection par mot de passe sur les documents Office](../vsto/password-protection-on-office-documents.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
