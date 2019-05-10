---
title: Validation de votre système pendant le développement
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fb9810f1c212dfb881f5725676a79c6307b9cfa
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476498"
---
# <a name="validate-your-system-during-development"></a>Validation de votre système pendant le développement

Visual Studio peut aider à garder votre logiciel en cohérence avec les besoins des utilisateurs et avec l’architecture de votre système.

Pour connaître les versions de Visual Studio qui prennent en charge chacune de ces fonctionnalités, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Tâches clés

Utilisez les tâches suivantes pour valider votre logiciel :

|**Tâches**|**Rubriques associées**|
|-|-|
|**Assurez-vous que votre logiciel répond aux besoins des utilisateurs**:<br /><br />Utilisez les spécifications et les modèles architectures pour vous aider à organiser les tests de votre système et ses composants. Cette pratique vous permet de vous assurer que vous testez les besoins importants des utilisateurs et des autres parties prenantes, et vous aide à mettre rapidement à jour les tests quand les besoins changent.|- [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md)|
|**Assurez-vous que votre logiciel reste cohérent avec la conception prévue de votre système :**<br /><br />Diagrammes de dépendance décrivent les dépendances prévues entre les composants de votre application. Pendant le développement, vous pouvez vérifier que les dépendances actuelles dans le code sont conformes à la conception prévue.|- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Ressources externes

|**Catégorie**|**Liens**|
|-|-|
|**Vidéos**|![lien vers la vidéo](../data-tools/media/playvideo.gif) [Channel 9 : Doug Seven : Compréhension du code et conception des systèmes avec Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![lien vers la vidéo](../data-tools/media/playvideo.gif) [Channel 9 : Architecture d’une Application](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Forums**|- [Outils de visualisation et de modélisation Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Extensibilité de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Voir aussi

- [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)
- [Analyser et modéliser l’architecture](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
