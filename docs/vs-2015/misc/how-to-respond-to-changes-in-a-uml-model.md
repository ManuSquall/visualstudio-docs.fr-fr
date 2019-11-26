---
title: 'Comment : répondre à des modifications dans un modèle UML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293401"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Comment : répondre à des modifications dans un modèle UML
Il est possible d'écrire du code qui s'exécute chaque fois qu'une modification se produit dans un modèle UML dans Visual Studio. Ce code répond de manière égale aux modifications apportées directement par l'utilisateur et par d'autres extensions Visual Studio. Pour connaître les versions de Visual Studio qui prennent en charge les modèles UML, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Ces techniques ne sont pas prises en charge par l'API UML. Elles risquent de ne pas fonctionner dans les futures versions de Visual Studio.

## <a name="see-also"></a>Voir aussi
 [Naviguer dans les gestionnaires d’événements de modèle UML](../modeling/navigate-the-uml-model.md) [propager les modifications en dehors de l'](../modeling/event-handlers-propagate-changes-outside-the-model.md) [exemple de modèle : couleur par stéréotype](https://go.microsoft.com/fwlink/?LinkId=213841)