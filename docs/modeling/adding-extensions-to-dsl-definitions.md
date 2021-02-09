---
title: Ajout d'extensions à des définitions DSL
description: Découvrez comment l’extension de définition DSL vous permet de créer un package d’extensions dans un langage spécifique à un domaine (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1208c152534206a0ed2894fc0e41d844e0b77d47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861957"
---
# <a name="add-extensions-to-dsl-definitions"></a>Ajouter des extensions à des définitions DSL

L’extension de définition DSL vous permet de créer un package d’extensions dans un langage spécifique à un domaine (DSL). L’extension DSL, qui est contenue dans une extension d’intégration Visual Studio (VSIX), peut être installée sur l’ordinateur d’un utilisateur de la même manière qu’une solution DSL. Les fonctionnalités supplémentaires peuvent être activées et désactivées de manière dynamique au moment de l’exécution. Les DSL n’ont pas besoin d’être explicitement conçus pour l’extension, et les extensions peuvent être conçues ultérieurement, ou par des tiers, sans modifier le DSL étendu.

Les extensions DSL peuvent inclure les fonctionnalités suivantes :

- Propriétés des éléments de modèle et de présentation

- Éléments décoratifs pour les formes et les connecteurs

- Classes, relations, formes et connecteurs

- Contraintes de validation

- Onglets et éléments de boîte à outils

Un utilisateur d’un DSL étendu peut créer et enregistrer un modèle qui contient des instances des fonctionnalités supplémentaires. Le modèle peut être lu par d’autres utilisateurs qui ont installé l’extension appropriée. Les utilisateurs qui n’ont pas installé l’extension ne peuvent pas utiliser les fonctionnalités supplémentaires, mais ils peuvent mettre à jour et enregistrer un modèle sans perdre les fonctionnalités supplémentaires.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi

- [Billets de blog connexes](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
