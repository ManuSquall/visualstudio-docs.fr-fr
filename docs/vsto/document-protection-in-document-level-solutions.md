---
title: Protection des documents dans les solutions au niveau du document
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 03724e523c1f49277e0bc2b23465d5296d806695
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648533"
---
# <a name="document-protection-in-document-level-solutions"></a>Protection des documents dans les solutions au niveau du document
  Vous pouvez utiliser les fonctionnalités de protection de Microsoft Office Word et Microsoft Office Excel dans les projets au niveau du document. Ces fonctionnalités bloquent les utilisateurs non autorisés d’apporter des modifications à des parties d’un document protégés.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 À l’aide d’Excel, vous pouvez activer protection sur et hors tension pendant que le classeur est ouvert dans le concepteur. À l’aide de Word, vous pouvez activer protection uniquement en dehors du concepteur. Lors de l’exécution, vous pouvez activer ou désactiver la protection par programmation de Word et Excel.  
  
 Lorsque la protection de document est activée sur un document est ouvert dans le concepteur, tous les contrôles sont supprimés à partir de la **boîte à outils** ou deviennent indisponibles, et vous ne pouvez pas faire glisser quoi que ce soit à partir de la **des Sources de données** fenêtre de document.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument et des documents protégés  
 Si un document est protégé, le cache de données n’est pas accessible à partir de hors du document. Vous ne pouvez pas utiliser le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour récupérer ou manipuler des données mises en cache dans un document protégé, ou utiliser d’autres méthodes de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> classe.  
  
## <a name="word-document-protection-in-the-designer"></a>Protection des documents Word dans le Concepteur  
 Si vous ajoutez une protection à un document Word ou un modèle lorsqu’il est ouvert dans Visual Studio, vous ne peut pas démarrer l’application de la protection dans le concepteur. Le document est en mode design pendant qu’il est ouvert dans Visual Studio, et il doit être en cours d’exécution avant de démarrer l’application de protection.  
  
 Toutefois, si vous créez un projet qui utilise un document Word existant qui est protégé, le document est protégé pendant l’ouverture dans le concepteur. Vous ne pouvez pas modifier les parties protégées du document, mais vous pouvez toujours écrire du code dans l’éditeur de Code pour automatiser le document. Vous ne pouvez pas générer le projet si la protection est activée lorsque le document est ouvert dans Visual Studio.  
  
 Vous pouvez désactiver la protection pendant que le document est ouvert dans le concepteur afin que vous pouvez modifier le document et générez le projet. Vous ne pouvez pas désactiver la protection pour la copie dans le concepteur pendant le débogage ; le document qui s’ouvre pendant le débogage est une copie distincte de celui qui est ouvert dans le concepteur (la copie de la sortie est stockée dans le *\bin* répertoire pour Visual Basic et le *\bin\debug* répertoire pour C# ).  
  
 Vous pouvez activer la protection sur la copie du document qui s’ouvre dans le Concepteur de fermeture du projet dans Visual Studio, ouvrez la copie du document qui se trouve dans le répertoire du projet, puis activer la protection.  
  
## <a name="enforce-word-document-protection-on-build"></a>Appliquer la protection de document Word sur la build  
 Visual Studio démarre l’application de protection des documents Word et des modèles pendant le processus de génération, afin que la protection est activée lorsque le document s’ouvre pour le débogage. Le document est protégé par un mot de passe vide.  
  
 La protection est activée pendant la génération donc que si le document contient du code <xref:Microsoft.Office.Tools.Word.Document.Startup> événements susceptibles de provoquer des exceptions ou de modifier le comportement de l’application, ce code peut être débogué correctement. Si vous activez la protection une fois que le document est ouvert, le code d’initialisation ne peut pas être débogué ou testé.  
  
## <a name="setting-the-password"></a>Le mot de passe  
 Visual Studio permet la protection automatiquement, mais ne fournit aucun mot de passe par défaut. Si vous souhaitez que la protection de document pour avoir un mot de passe, vous devez l’ajouter avant de déployer votre solution. Ajout d’un mot de passe vous permet de laisser les utilisateurs autorisés de supprimer la protection du document ; sans mot de passe, la protection ne peut pas être facilement supprimée. Pour plus d’informations sur la définition d’un mot de passe, consultez l’aide de l’application Office spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Protéger des documents et des parties de documents par programmation](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information rights management et vue d’ensemble des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protection de mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Guide pratique pour Autoriser le code de s’exécuter derrière des documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  