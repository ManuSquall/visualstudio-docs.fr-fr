---
title: Action rapide Ajouter un paramètre à une méthode
ms.date: 09/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3e1461afe5c4d6026f8532896ba837e971fed652
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934352"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Ajouter un paramètre à une méthode avec une Action rapide

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** permet d’ajouter automatiquement un paramètre à une méthode, en fonction de l’utilisation.

**Quand :** vous souhaitez ajouter un paramètre à une méthode et le déclarer correctement et automatiquement.

**Pourquoi :** vous pourriez ajouter le paramètre à la déclaration de méthode avant de l’appeler, mais cette fonctionnalité l’ajoute automatiquement sur la base d’un appel de méthode.

## <a name="how-to-use-it"></a>Utilisation

1. Ajoutez un argument supplémentaire à un appel de méthode.

   Une ligne rouge « ondulée » apparaît sous le nom de la méthode à l’endroit où vous l’appelez.

2. Placez votre pointeur sur la ligne rouge « ondulée » jusqu’à ce que le menu Actions rapides s’affiche. Cliquez sur la **flèche vers le bas** dans le menu Actions rapides, puis sélectionnez **Ajouter un paramètre à [méthode]**.

   ![Action rapide Ajouter un paramètre à une méthode dans Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Vous pouvez également accéder au menu Actions rapides en plaçant votre curseur sur la ligne de l’appel de méthode, puis en appuyant sur **Ctrl**+**.** ou en sélectionnant l’icône Ampoule dans la marge du fichier.

   Visual Studio ajoute le nouveau paramètre à la déclaration de méthode.

> [!NOTE]
> S’il existe d’autres appels de la méthode, ils risquent de produire des erreurs après cette Action rapide, car ils ne spécifient pas d’argument pour le paramètre qui vient d’être ajouté.

## <a name="see-also"></a>Voir aussi

- [Ajouter un paramètre à un constructeur](generate-constructor.md#addparameter)