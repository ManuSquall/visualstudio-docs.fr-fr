---
title: Protection des documents dans les solutions au niveau du document
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c5f019907495c3cad3fddef501455aedf345bb2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253804"
---
# <a name="document-protection-in-document-level-solutions"></a>Protection des documents dans les solutions au niveau du document
  Vous pouvez utiliser les fonctionnalités de protection de Microsoft Office Word et Microsoft Office Excel dans des projets au niveau du document. Ces fonctionnalités empêchent les utilisateurs non autorisés d’apporter des modifications aux parties protégées d’un document.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 À l’aide d’Excel, vous pouvez activer ou désactiver la protection lorsque le classeur est ouvert dans le concepteur. À l’aide de Word, vous pouvez activer la protection uniquement en dehors du concepteur. Au moment de l’exécution, vous pouvez activer ou désactiver la protection par programme à la fois pour Word et Excel.

 Lorsque la protection de document est activée sur un document ouvert dans le concepteur, tous les contrôles sont supprimés de la **boîte à outils** ou deviennent indisponibles, et vous ne pouvez pas faire glisser quoi que ce soit depuis la fenêtre **sources de données** vers le document.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument et documents protégés
 Si un document est protégé, le cache de données n’est pas accessible à partir de l’extérieur du document. Vous ne pouvez pas <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> utiliser la classe pour récupérer ou manipuler des données mises en cache dans un document protégé, ou utiliser d’autres <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> méthodes de la classe.

## <a name="word-document-protection-in-the-designer"></a>Protection des documents Word dans le concepteur
 Si vous ajoutez une protection à un modèle ou un document Word alors qu’il est ouvert dans Visual Studio, vous ne pouvez pas commencer à appliquer la protection dans le concepteur. Le document est en mode création alors qu’il est ouvert dans Visual Studio et doit être en mode exécution pour que vous puissiez commencer à appliquer la protection.

 Toutefois, si vous créez un projet qui utilise un document Word existant pour lequel la protection est activée, le document est protégé pendant qu’il est ouvert dans le concepteur. Vous ne pouvez pas modifier les parties protégées du document, mais vous pouvez toujours écrire du code dans l’éditeur de code pour automatiser le document. Vous ne pouvez pas non plus générer le projet si la protection est activée alors que le document est ouvert dans Visual Studio.

 Vous pouvez désactiver la protection lorsque le document est ouvert dans le concepteur afin que vous puissiez modifier le document et générer le projet. Vous ne pouvez pas désactiver la protection pour la copie dans le concepteur pendant le débogage. le document qui s’ouvre pendant le débogage est une copie distincte de celle ouverte dans le concepteur (la copie de sortie est stockée dans le répertoire *\Bin* pour Visual Basic et le répertoire \bin\Debug C#pour).

 Vous pouvez activer la protection sur la copie du document qui s’ouvre dans le concepteur en fermant le projet dans Visual Studio, en ouvrant la copie du document qui se trouve dans le répertoire du projet et en activant la protection.

## <a name="enforce-word-document-protection-on-build"></a>Appliquer la protection des documents Word lors de la génération
 Visual Studio commence à appliquer la protection des documents et des modèles Word pendant le processus de génération, afin que la protection soit activée lorsque le document s’ouvre pour le débogage. Le document est protégé par un mot de passe vide.

 La protection est activée pendant la génération. ainsi, si un code dans <xref:Microsoft.Office.Tools.Word.Document.Startup> l’événement de document peut provoquer des exceptions ou modifier le comportement de l’application, ce code peut être débogué correctement. Si vous activez la protection après l’ouverture du document, le code d’initialisation ne peut pas être débogué ou testé.

## <a name="setting-the-password"></a>Définition du mot de passe
 Visual Studio active automatiquement la protection, mais ne fournit pas de mot de passe par défaut. Si vous souhaitez que la protection de document ait un mot de passe, vous devez l’ajouter avant de déployer votre solution. L’ajout d’un mot de passe vous permet de permettre aux utilisateurs autorisés de supprimer la protection du document ; sans mot de passe, la protection ne peut pas être facilement supprimée. Pour plus d’informations sur la définition d’un mot de passe, consultez l’aide dans l’application Office spécifique.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Protéger des documents et des parties de documents par programmation](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Présentation de la gestion des droits relatifs à l’information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protection par mot de passe sur les documents Office](../vsto/password-protection-on-office-documents.md)
- [Guide pratique pour Autoriser le code à s’exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
