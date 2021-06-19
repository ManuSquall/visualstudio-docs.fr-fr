---
title: Validation de votre système pendant le développement
description: Découvrez comment Visual Studio peut vous aider à maintenir la cohérence de vos logiciels avec les exigences des utilisateurs et avec l’architecture de votre système.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae85c7f98aab3e852a810976cc1cecbd83b65307
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388371"
---
# <a name="validate-your-system-during-development"></a>Validation de votre système pendant le développement

Visual Studio peut vous aider à maintenir la cohérence de vos logiciels avec les exigences des utilisateurs et avec l’architecture de votre système.

Pour connaître les versions de Visual Studio qui prennent en charge chacune de ces fonctionnalités, consultez [Version support for architecture and modeling tools](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="key-tasks"></a>Tâches clés

Utilisez les tâches suivantes pour valider votre logiciel :

|**Tâches**|**Rubriques associées**|
|-|-|
|**Assurez-vous que votre logiciel répond aux besoins des utilisateurs**:<br /><br />Utilisez les spécifications et les modèles architecturaux pour vous aider à organiser les tests de votre système et de ses composants. Cette pratique vous permet de vous assurer que vous testez les besoins importants des utilisateurs et des autres parties prenantes, et vous aide à mettre rapidement à jour les tests quand les besoins changent.|- [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md)|
|**Assurez-vous que votre logiciel reste cohérent avec la conception prévue de votre système :**<br /><br />Les diagrammes de dépendance décrivent les dépendances prévues entre les composants de votre application. Pendant le développement, vous pouvez vérifier que les dépendances actuelles dans le code sont conformes à la conception prévue.|- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Ressources externes

|**Catégorie**|**Liens**|
|-|-|
|**Vidéos**|![lien vers la vidéo ](../data-tools/media/playvideo.gif) [Channel 9 : Doug sept : compréhension du code et conception de systèmes avec Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![lien vers la vidéo ](../data-tools/media/playvideo.gif) [Channel 9 : architecture d’une application](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Forums**|- [Outils de visualisation et de modélisation Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Extensibilité de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Voir aussi

- [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)
- [Architecture d’analyse et de modèle](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
