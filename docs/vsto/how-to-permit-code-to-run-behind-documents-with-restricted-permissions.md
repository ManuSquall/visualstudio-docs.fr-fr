---
title: Autoriser le code à s’exécuter derrière des documents avec des autorisations restreintes
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 14c468a806160fd31c84b164a4b995f904e71fc6
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298487"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Comment : autoriser le code à s’exécuter derrière des documents avec des autorisations restreintes
  Vous pouvez utiliser la fonctionnalité de Rights Management d’informations (IRM) de Microsoft Office pour restreindre les autorisations d’accès à un document ou à un classeur. Par défaut, le code derrière un document Word restreint Microsoft Office ou Microsoft Office classeur Excel n’est pas autorisé à s’exécuter. Vous pouvez modifier la valeur par défaut afin que vos extensions de code managé puissent accéder au modèle objet et que votre solution fonctionne.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Vous devez être l’auteur du document ou du classeur, ou disposer d’un accès contrôle total pour pouvoir modifier les paramètres d’autorisation.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Pour permettre au code de s’exécuter derrière des documents avec des autorisations restreintes

1. Ouvrez le document ou le classeur dans Word ou Excel.

2. Cliquez sur l’onglet **fichier** , pointez sur **préparer**, pointez sur **restreindre l’autorisation**, puis cliquez sur **accès restreint**.

   > [!NOTE]
   > Lors de la première utilisation, vous êtes invité à installer le client Windows Rights Management. Après avoir installé le client, vous devrez peut-être répéter les étapes.

3. Dans la boîte de dialogue **autorisation** , sélectionnez **restreindre l’autorisation à ce document**, puis cliquez sur **autres options**.

4. Sous **autorisations supplémentaires pour les utilisateurs**, sélectionnez **accéder au contenu par programme**.

   Word ou Excel autorise l’accès par programme au modèle objet.

## <a name="see-also"></a>Voir aussi
- [Présentation de la gestion des droits relatifs à l’information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)
- [Protection par mot de passe sur les documents Office](../vsto/password-protection-on-office-documents.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
