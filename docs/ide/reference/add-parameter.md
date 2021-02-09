---
title: Action rapide Ajouter un paramètre à une méthode
description: Découvrez comment utiliser une action rapide pour ajouter et déclarer automatiquement un paramètre, en fonction de l’utilisation, sur une méthode.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c1e623bea0eab4b45aec3d331864db49a2787f8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846346"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Ajouter un paramètre à une méthode avec une Action rapide

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** permet d’ajouter automatiquement un paramètre à une méthode, selon l’utilisation.

**Quand :** vous souhaitez ajouter un paramètre à une méthode et le déclarer correctement et automatiquement.

**Pourquoi :** vous pourriez ajouter le paramètre à la déclaration de méthode avant de l’appeler, mais cette fonctionnalité l’ajoute automatiquement sur la base d’un appel de méthode.

## <a name="how-to-use-it"></a>Comment l’utiliser

1. Ajoutez un argument supplémentaire à un appel de méthode.

   Un tilde rouge apparaît sous le nom de la méthode où vous l’appelez.

2. Placez le pointeur sur le tilde rouge jusqu’à ce que le menu actions rapides s’affiche. Cliquez sur la **flèche vers le bas** dans le menu Actions rapides, puis sélectionnez **Ajouter un paramètre à [méthode]**.

   ![Action rapide Ajouter un paramètre à une méthode dans Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Vous pouvez également accéder au menu actions rapides en plaçant votre curseur sur la ligne de l’appel de méthode, puis en appuyant sur **CTRL** + **.** (point) ou en sélectionnant l’icône d’ampoule dans la marge de fichier.

   Visual Studio ajoute le nouveau paramètre à la déclaration de méthode.

> [!NOTE]
> S’il existe d’autres appels de la méthode, ils risquent de produire des erreurs après cette Action rapide, car ils ne spécifient pas d’argument pour le paramètre qui vient d’être ajouté.

## <a name="see-also"></a>Voir aussi

- [Ajouter un paramètre à un constructeur](generate-constructor.md#addparameter)
