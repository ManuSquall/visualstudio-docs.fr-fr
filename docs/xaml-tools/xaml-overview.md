---
title: Vue d’ensemble du langage XAML
ms.date: 07/31/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9b04012e2f0b046b3fd31058c9838740e833281
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450890"
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

## <a name="see-also"></a>Voir aussi

- [XAML dans les applications WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)