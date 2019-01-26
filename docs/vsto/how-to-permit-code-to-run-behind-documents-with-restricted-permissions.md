---
title: 'Procédure : Autoriser le code de s’exécuter derrière des documents avec des autorisations restreintes'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6030165e7b24bdba5c7fa6e223b915e5cf4c85c8
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870254"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Procédure : Autoriser le code de s’exécuter derrière des documents avec des autorisations restreintes
  Vous pouvez utiliser la fonctionnalité Information Rights Management (IRM) de Microsoft Office pour restreindre les autorisations à un document ou classeur. Par défaut, le code derrière un document Microsoft Office Word restreint ou un classeur Microsoft Office Excel n’est pas autorisé à exécuter. Vous pouvez modifier la valeur par défaut afin que vos extensions de code managé peuvent accéder au modèle objet, et votre solution fonctionnera.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous devez être l’auteur du document ou classeur ou ont un accès contrôle total pour pouvoir modifier les paramètres d’autorisation.  
  
## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Pour autoriser le code de s’exécuter derrière des documents avec des autorisations restreintes  
  
1. Ouvrez le document ou le classeur dans Word ou Excel.  
  
2. Cliquez sur le **fichier** onglet, pointez sur **préparation**, pointez sur **restreindre l’autorisation**, puis cliquez sur **accès restreint**.  
  
   > [!NOTE]  
   >  À la première utilisation, vous êtes invité à installer le client Windows Rights Management. Après avoir installé le client, vous devrez peut-être répéter ces étapes.  
  
3. Dans le **autorisation** boîte de dialogue, sélectionnez **restreindre l’autorisation à ce document**, puis cliquez sur **plus d’Options**.  
  
4. Sous **des autorisations supplémentaires pour les utilisateurs**, sélectionnez **accéder par programmation au contenu**.  
  
   Word ou Excel autorise un accès par programmation au modèle objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Information rights management et vue d’ensemble des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Protection de mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)  
