---
title: Création d’une fenêtre d’outil multi-instance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 687d46136ad4ed0f043210839e95caf6071f87f2
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317482"
---
# <a name="create-a-multi-instance-tool-window"></a>Créer une fenêtre d’outil multi-instance
Vous pouvez programmer une fenêtre outil afin que plusieurs instances de celui-ci peuvent être ouverts simultanément. Par défaut, les fenêtres Outil peuvent avoir qu’une seule instance ouvrir.

Lorsque vous utilisez une fenêtre outil à instances multiples, vous pouvez afficher plusieurs sources associées d’informations en même temps. Par exemple, vous pouvez placer un multiligne <xref:System.Windows.Forms.TextBox> contrôle dans une fenêtre outil à instances multiples de sorte que plusieurs extraits de code sont disponibles simultanément pendant une session de programmation. En outre, par exemple, vous pouvez placer un <xref:System.Windows.Forms.DataGrid> contrôle et une liste déroulante, zone dans une fenêtre d’outil multi-instance afin que plusieurs sources de données en temps réel peuvent être suivis simultanément.

## <a name="create-a-basic-single-instance-tool-window"></a>Créer une fenêtre outil de base (uniques)

1. Créez un projet nommé **MultiInstanceToolWindow** en utilisant le modèle VSIX et ajouter un modèle d’élément de fenêtre outil personnalisé nommé **MIToolWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Créer une instance de multiples de fenêtre outil

1. Ouvrez le *MIToolWindowPackage.cs* de fichiers et de trouver le `ProvideToolWindow` attribut. et le `MultiInstances=true` paramètre, comme indiqué dans l’exemple suivant :

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Dans le *MIToolWindowCommand.cs* de fichiers, recherchez le `ShowToolWindos()` (méthode). Dans cette méthode, appelez le <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> (méthode) et définissez son `create` indicateur `false` afin qu’il effectue une itération dans les instances de la fenêtre Outil existantes jusqu'à une disponible `id` est trouvé.

3. Pour créer une instance de la fenêtre outil, appelez le <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> (méthode) et définissez son `id` à des valeurs disponibles et ses `create` indicateur `true`.

    Par défaut, la valeur de la `id` paramètre de la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> méthode est `0`. Cette valeur, une fenêtre outil à instance unique. Pour plus d’une instance d’héberger, chaque instance doit avoir son propre `id`.

4. Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui est retourné par la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> propriété de l’instance de la fenêtre outil.

5. Par défaut, le `ShowToolWindow` méthode qui est créé par le modèle d’élément de fenêtre outil crée une fenêtre outil à instance unique. L’exemple suivant montre comment modifier le `ShowToolWindow` méthode pour créer plusieurs instances.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
