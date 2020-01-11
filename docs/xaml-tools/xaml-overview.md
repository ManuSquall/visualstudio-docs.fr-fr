---
title: Vue d’ensemble du langage XAML
ms.date: 01/09/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 28f630ccaa126c7d8cfc8870e234111b51e1afd2
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75866143"
---
# <a name="overview-of-xaml"></a>Vue d’ensemble du langage XAML

Le langage XAML est un langage déclaratif basé sur XML. Il est largement utilisé dans les types d’applications suivants pour créer des interfaces utilisateur :

- [Applications Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Applications de la plateforme Windows universelle (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

Le code XAML suivant définit un contrôle bouton simple.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

Le langage XAML est également utilisé pour définir des workflows dans les [applications Windows WorkFlow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-designer"></a>Concepteur XAML

Visual Studio et Blend pour Visual Studio fournissent un concepteur XAML qui permet de générer des interfaces utilisateur pour les applications WPF, UWP et Xamarin.Forms. Vous pouvez faire glisser des contrôles à partir de la fenêtre Boîte à outils ou Composants, et définir des propriétés dans la fenêtre Propriétés. Quand vous effectuez ces actions, Visual Studio et Blend pour Visual Studio créent le code XAML correspondant. Si vous préférez modifier le code XAML directement, vous le pouvez.

Les articles de cette documentation abordent le concepteur XAML de Visual Studio et de Blend pour Visual Studio.

## <a name="whats-new"></a>Nouveautés

Pour obtenir les informations les plus récentes, consultez le billet de blog [Nouveautés dans les outils de développement XAML dans Visual studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) , ou regardez la vidéo la plus récente, [nouvelles fonctionnalités XAML dans Visual Studio](https://youtu.be/yI9OyA4ZM2E), sur YouTube.

## <a name="see-also"></a>Voir aussi

- [XAML dans les applications WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
