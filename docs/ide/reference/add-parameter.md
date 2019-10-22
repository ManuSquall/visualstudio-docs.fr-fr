---
title: Action rapide Ajouter un paramètre à une méthode
ms.date: 09/28/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d1edc9d38ff4476a9fe76886676bfce1c80a61db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658805"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Ajouter un paramètre à une méthode avec une Action rapide

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** permet d’ajouter automatiquement un paramètre à une méthode, selon l’utilisation.

**Quand :** vous souhaitez ajouter un paramètre à une méthode et le déclarer correctement et automatiquement.

**Pourquoi :** vous pourriez ajouter le paramètre à la déclaration de méthode avant de l’appeler, mais cette fonctionnalité l’ajoute automatiquement sur la base d’un appel de méthode.

## <a name="how-to-use-it"></a>Utilisation

1. Ajoutez un argument supplémentaire à un appel de méthode.

   Un tilde rouge apparaît sous le nom de la méthode où vous l’appelez.

2. Placez le pointeur sur le tilde rouge jusqu’à ce que le menu actions rapides s’affiche. Cliquez sur la **flèche vers le bas** dans le menu Actions rapides, puis sélectionnez **Ajouter un paramètre à [méthode]** .

   ![Action rapide Ajouter un paramètre à une méthode dans Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Vous pouvez également accéder au menu Actions rapides en plaçant votre curseur sur la ligne de l’appel de méthode, puis en appuyant sur **Ctrl**+ **.** (point) ou en sélectionnant l’icône d’ampoule dans la marge de fichier.

   Visual Studio ajoute le nouveau paramètre à la déclaration de méthode.

> [!NOTE]
> S’il existe d’autres appels de la méthode, ils risquent de produire des erreurs après cette Action rapide, car ils ne spécifient pas d’argument pour le paramètre qui vient d’être ajouté.

## <a name="see-also"></a>Voir aussi

- [Ajouter un paramètre à un constructeur](generate-constructor.md#addparameter)