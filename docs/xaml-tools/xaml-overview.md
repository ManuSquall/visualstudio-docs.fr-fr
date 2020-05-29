---
title: Vue d’ensemble du langage XAML
ms.date: 05/20/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 97f3bc7777023903d5fc38ad1bda7cde45b683b6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183481"
---
# <a name="overview-of-xaml"></a>Vue d’ensemble du langage XAML

Le langage XAML est un langage déclaratif basé sur XML. Il est largement utilisé dans les types d’applications suivants pour créer des interfaces utilisateur :

- [Applications Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Applications plateforme Windows universelle (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

Le code XAML suivant définit un contrôle bouton simple.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

Le langage XAML est également utilisé pour définir des workflows dans les [applications Windows WorkFlow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-designer"></a>Concepteur XAML

Visual Studio et Blend pour Visual Studio fournissent un concepteur XAML qui permet de générer des interfaces utilisateur pour les applications WPF, UWP et Xamarin.Forms. Vous pouvez faire glisser des contrôles à partir de la fenêtre Boîte à outils ou Composants, et définir des propriétés dans la fenêtre Propriétés. Dans ce cas, Visual Studio et Blend pour Visual Studio créent le code XAML correspondant. Si vous préférez modifier le code XAML directement, vous le pouvez.

Les articles de cette documentation abordent le concepteur XAML de Visual Studio et de Blend pour Visual Studio.

## <a name="whats-new"></a>Nouveautés

Pour obtenir les informations les plus récentes, consultez le billet de blog [Nouveautés dans les outils de développement XAML dans Visual studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) , les [améliorations apportées aux outils XAML dans le billet de blog Visual studio 2019 version 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/) , ainsi que les [nouvelles fonctionnalités XAML de Visual Studio](https://youtu.be/yI9OyA4ZM2E) Video sur YouTube.

## <a name="see-also"></a>Voir aussi

- [XAML dans les applications WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
