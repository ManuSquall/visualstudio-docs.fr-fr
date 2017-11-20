---
title: "Comment : permettre au Code de s’exécuter derrière des Documents avec des autorisations restreintes | Documents Microsoft"
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
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d5ab02ea2eb2d34a82607b8f7fd4fbf3f02dd76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Comment : permettre au code de s'exécuter derrière des documents dotés d'autorisations restreintes
  Vous pouvez utiliser la fonctionnalité Information Rights Management (IRM) de Microsoft Office pour limiter les autorisations à un document ou le classeur. Par défaut, le code derrière un document Microsoft Office Word restreint ou un classeur Microsoft Office Excel n’est pas autorisé à s’exécuter. Vous pouvez modifier la valeur par défaut afin que vos extensions de code managé peuvent accéder au modèle objet, et que votre solution ne fonctionnera pas.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous devez être l’auteur du document ou classeur ou avoir accès en contrôle total pour pouvoir modifier les paramètres d’autorisation.  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Pour permettre au code à exécuter derrière des documents avec des autorisations restreintes  
  
1.  Ouvrez le document ou le classeur dans Word ou Excel.  
  
2.  Cliquez sur le **fichier** onglet, pointez sur **préparation**, pointez sur **restreindre l’autorisation**, puis cliquez sur **accès restreint**.  
  
    > [!NOTE]  
    >  La première utilisation, vous êtes invité à installer le client Windows Rights Management. Après avoir installé le client, vous devrez peut-être répéter les étapes.  
  
3.  Dans le **autorisation** boîte de dialogue, sélectionnez **restreindre l’autorisation à ce document**, puis cliquez sur **plus d’Options**.  
  
4.  Sous **des autorisations supplémentaires pour les utilisateurs**, sélectionnez **accéder par programme au contenu**.  
  
 Word ou Excel autorise l’accès par programme au modèle objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Information Rights Management et vue d’ensemble des Extensions de Code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protection des documents dans les Solutions au niveau du Document](../vsto/document-protection-in-document-level-solutions.md)   
 [Mot de passe sur des Documents Office](../vsto/password-protection-on-office-documents.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d’une solution Office](../vsto/deploying-an-office-solution.md)  
  
  