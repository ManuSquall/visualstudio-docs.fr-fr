---
title: Protection dans les Solutions au niveau du Document des documents | Documents Microsoft
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 546a74179b8bdf52541d771809426b5e4aec3e45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="document-protection-in-document-level-solutions"></a>Protection des documents dans les solutions au niveau du document
  Vous pouvez utiliser les fonctionnalités de protection de Microsoft Office Word et Microsoft Office Excel dans les projets au niveau du document. Ces fonctionnalités empêchent les utilisateurs non autorisés d’apporter des modifications à des parties d’un document protégés.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 À l’aide d’Excel, vous pouvez activer protection sur et hors tension pendant que le classeur est ouvert dans le concepteur. À l’aide de Word, vous pouvez activer protection uniquement en dehors du concepteur. Au moment de l’exécution, vous pouvez activer ou désactiver la protection par programmation pour Word et Excel.  
  
 Lorsque la protection de document est activée sur un document est ouvert dans le concepteur, tous les contrôles sont supprimés à partir de la **boîte à outils** ou deviennent indisponibles, et vous ne pouvez pas faire glisser quoi que ce soit à partir de la **des Sources de données** fenêtre de document.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument et des Documents protégés  
 Si un document est protégé, le cache de données ne sont pas accessibles à partir d’en dehors du document. Vous ne pouvez pas utiliser le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour récupérer ou manipuler des données mises en cache dans un document protégé, ou utiliser d’autres méthodes de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> classe.  
  
## <a name="word-document-protection-in-the-designer"></a>Protection des documents Word dans le Concepteur  
 Si vous ajoutez une protection à un document Word ou un modèle lorsqu’il est ouvert dans Visual Studio, vous ne peut pas démarrer l’application de la protection dans le concepteur. Le document est en mode design pendant qu’il est ouvert dans Visual Studio, et il doit être en cours d’exécution avant de démarrer l’application de protection.  
  
 Toutefois, si vous créez un projet qui utilise un document Word existant qui est protégé, le document est protégé ouvert dans le concepteur. Vous ne pouvez pas modifier les parties protégées du document, mais vous pouvez toujours écrire du code dans l’éditeur de Code pour automatiser le document. Vous ne pouvez pas générer le projet si la protection est activée alors que le document est ouvert dans Visual Studio.  
  
 Vous pouvez désactiver la protection pendant que le document est ouvert dans le concepteur afin que vous pouvez modifier le document et générez le projet. Vous ne pouvez pas désactiver la protection de la copie dans le concepteur pendant le débogage ; le document qui s’ouvre pendant le débogage est une copie distincte de celui qui est ouvert dans le concepteur (la copie de la sortie est stockée dans le répertoire \bin pour Visual Basic et le répertoire \bin\debug pour c#).  
  
 Vous pouvez activer la protection sur la copie du document qui s’ouvre dans le concepteur en fermant le projet dans Visual Studio, en ouvrant la copie du document qui se trouve dans le répertoire du projet et l’activation de la protection.  
  
## <a name="enforcing-word-document-protection-on-build"></a>Activer la Protection de Document Word lors de la Build  
 Visual Studio démarre l’application de protection des documents Word et des modèles pendant le processus de génération, afin que la protection est activée lorsque le document s’ouvre pour le débogage. Le document est protégé par un mot de passe vide.  
  
 La protection est activée lors de la génération par conséquent, si le document contient du code <xref:Microsoft.Office.Tools.Word.Document.Startup> événements susceptibles de provoquer des exceptions ou de modifier le comportement de l’application, ce code peut être débogué correctement. Si vous activez la protection après l’ouverture du document, le code d’initialisation ne peut pas être débogué ou testé.  
  
## <a name="setting-the-password"></a>Le mot de passe  
 Visual Studio permet la protection automatiquement, mais ne fournit aucun mot de passe par défaut. Si vous souhaitez que la protection du document d’avoir un mot de passe, vous devez l’ajouter avant de déployer votre solution. Ajout d’un mot de passe vous permet de laisser les utilisateurs autorisés de supprimer la protection du document ; sans un mot de passe ne peut pas être facilement supprimer la protection. Pour plus d’informations sur la définition d’un mot de passe, consultez l’aide de l’application Office spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : protéger des Documents et des parties de Documents par programmation](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information Rights Management et vue d’ensemble des Extensions de Code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Mot de passe sur des Documents Office](../vsto/password-protection-on-office-documents.md)   
 [Comment : permettre au Code de s’exécuter derrière des Documents avec des autorisations restreintes](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  