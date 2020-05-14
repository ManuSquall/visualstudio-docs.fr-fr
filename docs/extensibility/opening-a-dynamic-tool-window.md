---
title: Ouverture d’une fenêtre d’outil dynamique (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702257"
---
# <a name="open-a-dynamic-tool-window"></a>Ouvrez une fenêtre d’outil dynamique
Les fenêtres d’outils sont généralement ouvertes à partir d’une commande sur un menu, ou d’un raccourci clavier équivalent. Parfois, cependant, vous pourriez avoir besoin d’une fenêtre d’outil qui s’ouvre chaque fois qu’un contexte spécifique d’interface utilisateur s’applique, et se ferme lorsque le contexte de l’interface utilisateur ne s’applique plus. Ces types de fenêtres d’outils sont appelés *dynamiques* ou *auto-visibles.*

> [!NOTE]
> Pour une liste des contextes d’interface <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>utilisateur prédéfinis, voir .

 Si vous souhaitez ouvrir une fenêtre d’outil dynamique au démarrage, et qu’il est possible que la création échoue, vous devez implémenter l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> et tester les conditions de défaillance de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> méthode. Pour que la coque sache que vous avez une fenêtre d’outil dynamique `SupportsDynamicToolOwner` qui doit être ouverte au démarrage, vous devez ajouter la valeur (réglée à 1) à votre enregistrement de paquet. Cette valeur ne fait <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>pas partie de la norme, vous devez donc créer un attribut personnalisé pour l’ajouter. Pour plus d’informations sur les attributs personnalisés, voir [Utilisez un attribut d’enregistrement personnalisé pour enregistrer une extension](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Utilisez <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> pour ouvrir une fenêtre d’outil. La fenêtre d’outils est créée au besoin.

> [!NOTE]
> Une fenêtre d’outil dynamique peut être fermée par l’utilisateur. Si vous souhaitez créer une commande de menu afin que l’utilisateur puisse rouvrir la fenêtre de l’outil, la commande de menu doit être activée dans le même contexte d’interface utilisateur qui ouvre la fenêtre d’outil, et désactivé autrement.

## <a name="to-open-a-dynamic-tool-window"></a>Ouvrir une fenêtre d’outils dynamique

1. Créez un projet VSIX nommé **DynamicToolWindow** et ajoutez un modèle d’élément de fenêtre d’outil nommé *DynamicWindowPane.cs*. Pour plus d’informations, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

2. Dans le fichier *DynamicWindowPanePackage.cs,* trouvez la déclaration DynamicWindowPanePackage. Ajoutez <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> les <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> attributs et les attributs pour enregistrer la fenêtre d’outil.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Les attributs ci-dessus enregistrent la fenêtre d’outil nommée DynamicWindowPane comme une fenêtre transitoire qui n’est pas persistée lorsque Visual Studio est fermé et rouvert. DynamicWindowPane est <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ouvert chaque fois qu’il s’applique, et fermé autrement.

3. Générez le projet et commencez le débogage. L’instance expérimentale devrait apparaître. Vous ne devriez pas voir la fenêtre d’outil.

4. Ouvrez un projet dans le cas expérimental. La fenêtre d’outil doit apparaître.
