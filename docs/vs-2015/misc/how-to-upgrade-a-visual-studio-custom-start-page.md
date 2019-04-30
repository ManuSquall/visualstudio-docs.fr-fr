---
title: 'Procédure : Mise à niveau d’une Page de démarrage personnalisée | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: abe1013d37db43114f3970f12b1a0d1f08b07a4e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446454"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Procédure : Mise à niveau une Page de démarrage personnalisée Visual Studio
Vous pouvez mettre à niveau une page de démarrage personnalisée Visual Studio 2010 ou Visual Studio 2012 vers Visual Studio 2015 en procédant comme suit.

> [!WARNING]
> La page de démarrage personnalisée mise à niveau dans cette procédure est celle créée avec le modèle [Custom Start Page](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) disponible dans la galerie Visual Studio. Votre page de démarrage peut avoir d’autres fonctionnalités qui doivent être mises à niveau.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Pour mettre à niveau une page de démarrage personnalisée vers Visual Studio 2015

1. Vérifiez que Visual Studio 2015 et le Kit de développement logiciel (SDK) Visual Studio 2015 sont installés. Vous pouvez télécharger le Kit VSSDK à partir de la page [Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436).

2. Ouvrez votre projet de modèle personnalisé. Vous verrez un message vous informant que le projet doit être mis à niveau. Cliquez sur **OK** et attendez que la mise à niveau se termine.

3. Dans les propriétés du projet de page de démarrage et du projet de contrôle, vérifiez que l’infrastructure cible est au moins .NET Framework 4.5.

4. Dans la catégorie Debug des propriétés du projet de page de démarrage, définissez le chemin de la version Visual Studio 2015 de devenv.exe.

5. Dans les références de projet pour les deux projets, supprimez les références à Microsoft.VisualStudio.Shell.11.0 et ajoutez des références à Microsoft.VisualStudio.Shell.14.0.

6. Ouvrez StartPage.xaml avec l’éditeur XML et apportez les modifications suivantes :

    1. Mettez à jour les espaces de noms. Remplacez les lignes suivantes :

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         par les suivantes :

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Ouvrez MyControl.xaml, puis remplacez la référence d’espace de noms `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` par `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .