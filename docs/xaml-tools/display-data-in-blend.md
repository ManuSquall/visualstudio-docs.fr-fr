---
title: Visualiser des exemples de données dans une interface utilisateur XAML
titleSuffix: Blend for Visual Studio
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0614552bbbadd9a472e0780db6f277d423446966
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886453"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Afficher des données dans Blend pour Visual Studio

Vous pouvez afficher des exemples de données dans votre concepteur à mesure que vous personnalisez la disposition de vos pages. Vous pouvez générer des exemples de données de toutes pièces ou en utilisant une classe existante. Vous pouvez aussi vous connecter à des *données en direct* qui s’affichent dans votre application au moment où vous l’exécutez.

> [!NOTE]
> Le volet **données** dans Blend est pris en charge uniquement pour les projets qui ciblent .NET Framework. Elle n’est pas prise en charge pour les projets UWP ou les projets qui ciblent .NET Core. 

## <a name="generate-sample-data"></a>Générer un échantillon de données

Pour générer des exemples de données, ouvrez un document XAML. Dans le panneau **données** , choisissez le bouton **créer un exemple de données** ![créer un exemple d’icône de données](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png), puis choisissez **nouvel exemple de données**.

Définissez la structure de vos données dans le panneau **Données** et liez-la aux éléments d'interface utilisateur d'une page.

![Panneau Données](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Si vous souhaitez que vos exemples de données apparaissent dans vos pages lorsque vous exécutez l’application, choisissez **options de source de données** ![icône Options de source de données](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png), puis sélectionnez **activer lors**de l’exécution de l’application.

![Élément de menu Activer lorsque l’application est exécutée](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Regardez une brève vidéo :** ![icône de lecture](../designers/media/bldadminconsoleinitialconfigicon.PNG) [créer des exemples de données à partir de zéro](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

## <a name="generate-sample-data-from-a-class"></a>Générer des exemples de données à partir d'une classe

Si vous avez déjà créé des classes qui décrivent la structure de vos données, vous pouvez générer des exemples de données à partir de celles-ci.

Pour générer des exemples de données à partir d’une classe, ouvrez un document XAML, puis dans le volet **données** , cliquez sur le bouton **créer un exemple de données** ![créer un exemple de données](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) icône, puis cliquez sur créer un **exemple de données à partir de la classe**.

**Regardez une brève vidéo :** ![icône de lecture](../designers/media/bldadminconsoleinitialconfigicon.PNG) [combiner une liaison de données avec Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Voir aussi

- [Créer une IU à l’aide de Blend pour Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
