---
title: Vue d’ensemble du langage XAML
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331943"
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

## <a name="xaml-code-editor"></a>Éditeur de code XAML

L' [éditeur de code XAML](xaml-code-editor.md) dans l’IDE de Visual Studio comprend tous les outils dont vous avez besoin pour créer des applications WPF et UWP pour la plate-forme Windows, et pour Xamarin. Forms. Et bien que l’IDE (environnement de développement intégré) dans Visual Studio dispose de nombreuses fonctionnalités que vous pouvez utiliser pour développer des applications pour d’autres plateformes, il comporte également certaines fonctionnalités propres à XAML.

## <a name="xaml-designer"></a>Concepteur XAML

Visual Studio et Blend pour Visual Studio fournissent une [Concepteur XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) qui vous aide à générer des interfaces utilisateur pour les applications WPF, UWP et Xamarin. Forms. Vous pouvez faire glisser des contrôles à partir de la fenêtre Boîte à outils ou Composants, et définir des propriétés dans la fenêtre Propriétés. Dans ce cas, Visual Studio et Blend pour Visual Studio créent le code XAML correspondant. Si vous préférez modifier le code XAML directement, vous le pouvez.

## <a name="whats-new"></a>Nouveautés

Pour obtenir les informations les plus récentes, reportez-vous aux ressources suivantes :

- Les **[améliorations apportées aux outils XAML dans Visual Studio 2019 version 16,7 Preview 1 billet de](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)** blog
- Le billet de blog **[Nouveautés dans les outils de développement XAML dans Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- **[Nouvelles fonctionnalités XAML dans Visual Studio](https://youtu.be/yI9OyA4ZM2E)** Video sur YouTube

## <a name="see-also"></a>Voir aussi

- [XAML dans les applications WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
