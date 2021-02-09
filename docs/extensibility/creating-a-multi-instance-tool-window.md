---
title: Création d’une fenêtre outil à instances multiples | Microsoft Docs
description: Découvrez comment modifier une fenêtre outil afin que plusieurs instances de celle-ci puissent être ouvertes simultanément. Par défaut, une seule instance peut être ouverte pour les fenêtres outil.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1d332e3c41a55de8f405f028070fa95f97f6717
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923265"
---
# <a name="create-a-multi-instance-tool-window"></a>Créer une fenêtre outil à instances multiples
Vous pouvez programmer une fenêtre outil afin que plusieurs instances de celle-ci puissent être ouvertes simultanément. Par défaut, une seule instance peut être ouverte pour les fenêtres outil.

Lorsque vous utilisez une fenêtre outil à instances multiples, vous pouvez afficher plusieurs sources d’informations associées en même temps. Par exemple, vous pouvez placer un <xref:System.Windows.Forms.TextBox> contrôle sur plusieurs lignes dans une fenêtre outil multi-instance afin que plusieurs extraits de code soient disponibles simultanément pendant une session de programmation. Par exemple, vous pouvez placer un <xref:System.Windows.Forms.DataGrid> contrôle et une zone de liste déroulante dans une fenêtre outil à instances multiples afin que plusieurs sources de données en temps réel puissent être suivies simultanément.

## <a name="create-a-basic-single-instance-tool-window"></a>Créer une fenêtre outil de base (à instance unique)

1. Créez un projet nommé **MultiInstanceToolWindow** à l’aide du modèle VSIX, puis ajoutez un modèle d’élément de fenêtre outil personnalisé nommé **MIToolWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Rendre une fenêtre outil multi-instance

1. Ouvrez le fichier *MIToolWindowPackage.cs* et recherchez l' `ProvideToolWindow` attribut. et le `MultiInstances=true` paramètre, comme indiqué dans l’exemple suivant :

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Dans le fichier *MIToolWindowCommand.cs* , recherchez la `ShowToolWindos()` méthode. Dans cette méthode, appelez la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> méthode et affectez `create` à son indicateur la valeur `false` afin qu’elle itère au sein des instances de fenêtre outil existantes jusqu’à ce qu’un disponible `id` soit trouvé.

3. Pour créer une instance de fenêtre outil, appelez la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> méthode et affectez `id` à sa valeur disponible et à son indicateur la valeur `create` `true` .

    Par défaut, la valeur du `id` paramètre de la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> méthode est `0` . Cette valeur crée une fenêtre outil à instance unique. Pour l’hébergement de plusieurs instances, chaque instance doit avoir son propre unique `id` .

4. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode sur l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet retourné par la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> propriété de l’instance de la fenêtre outil.

5. Par défaut, la `ShowToolWindow` méthode créée par le modèle d’élément de la fenêtre outil crée une fenêtre outil à instance unique. L’exemple suivant montre comment modifier la `ShowToolWindow` méthode pour créer plusieurs instances.

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
