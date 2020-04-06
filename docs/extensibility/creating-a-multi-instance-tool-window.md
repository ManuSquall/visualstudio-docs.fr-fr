---
title: Création d’une fenêtre d’outils multi-instances (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739625"
---
# <a name="create-a-multi-instance-tool-window"></a>Créer une fenêtre d’outils multi-instances
Vous pouvez programmer une fenêtre d’outil de sorte que plusieurs instances de celui-ci peuvent être ouverts simultanément. Par défaut, les fenêtres d’outils ne peuvent avoir qu’une seule instance ouverte.

Lorsque vous utilisez une fenêtre d’outil multi-instance, vous pouvez afficher plusieurs sources d’information connexes en même temps. Par exemple, vous pouvez mettre <xref:System.Windows.Forms.TextBox> un contrôle multi-lignes dans une fenêtre d’outil multi-instances de sorte que plusieurs extraits de code sont simultanément disponibles au cours d’une session de programmation. En outre, par exemple, <xref:System.Windows.Forms.DataGrid> vous pouvez mettre un contrôle et une boîte de liste d’abandon dans une fenêtre d’outil multi-instances de sorte que plusieurs sources de données en temps réel peuvent être suivis simultanément.

## <a name="create-a-basic-single-instance-tool-window"></a>Créer une fenêtre d’outils de base (à instance unique)

1. Créez un projet nommé **MultiInstanceToolWindow** à l’aide du modèle VSIX, et ajoutez un modèle d’élément de fenêtre d’outil personnalisé nommé **MIToolWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre d’outil, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Faire une fenêtre d’outil multi-instance

1. Ouvrez le *fichier MIToolWindowPackage.cs* et `ProvideToolWindow` trouvez l’attribut. et `MultiInstances=true` le paramètre, comme le montre l’exemple suivant :

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Dans le *fichier MIToolWindowCommand.cs,* `ShowToolWindos()` trouvez la méthode. Dans cette méthode, <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> appelez la `create` méthode `false` et définissez son drapeau pour qu’il `id` s’enflaye à travers les instances existantes de fenêtre d’outil jusqu’à ce qu’un disponible soit trouvé.

3. Pour créer une vitrine d’outil, `id` appelez la méthode `create` et `true`définissez-la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> à une valeur disponible et son drapeau à .

    Par défaut, la `id` valeur du <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> paramètre de la méthode est `0`. Cette valeur fait une fenêtre d’outil à instance unique. Pour plus d’un exemple à accueillir, chaque `id`instance doit avoir son propre unique .

4. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> sur l’objet <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> qui est retourné par la propriété de l’instance de fenêtre d’outil.

5. Par défaut, `ShowToolWindow` la méthode créée par le modèle de fenêtre d’outil crée une fenêtre d’outil à instance unique. L’exemple suivant montre `ShowToolWindow` comment modifier la méthode pour créer plusieurs instances.

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
