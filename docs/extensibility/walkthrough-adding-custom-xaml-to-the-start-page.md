---
title: 'Procédure pas à pas : ajout de code XAML personnalisé à la page de démarrage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: a13aada6cca9b54d8469885ab4c314a89cd06d6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905955"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Procédure pas à pas : ajouter du code XAML personnalisé à la page de démarrage

Cette procédure pas à pas montre comment créer une page de démarrage Visual Studio personnalisée qui contient un navigateur Web.

## <a name="add-custom-xaml"></a>Ajouter du code XAML personnalisé

1. Créez une page de démarrage en suivant les instructions de la [page créer une page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).

2. Dans le fichier *MainWindow. Xaml* , recherchez la \<Grid> section.

3. Ajoutez un \<TabControl> élément et un \<TabItem> à l’intérieur de l' \< Grid> élément, comme indiqué dans l’exemple suivant.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Ajoutez un second \<TabItem> , avec un \<Button> élément qui ouvre un nouveau projet :

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Tester la page de démarrage personnalisée

1. Appuyez sur **F5**.

     L’instance expérimentale de Visual Studio s’ouvre, avec la page de démarrage personnalisée installée, mais non sélectionnée.

2. Dans l’instance expérimentale de Visual Studio, ouvrez la page **Outils/Options/environnement** .

3. Sélectionnez **démarrage**. Dans la liste **personnaliser la page de démarrage** , sélectionnez votre fichier *. Xaml* , puis cliquez sur **OK**.

4. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

5. Cliquez sur l’onglet **Bing** .

     Une page Web Bing doit s’afficher.

6. Cliquez sur l’onglet **MyButton** .

     Vous devez voir un bouton **MyProject** qui ouvre la boîte de dialogue **nouveau projet** .

7. Fermez l’instance expérimentale.

Pour appliquer la page de démarrage personnalisée, dans **Outils**  >  **options**  >  **environnement**, sélectionnez **démarrage**. Dans la liste **personnaliser la page de démarrage** , sélectionnez votre fichier *. Xaml* , puis cliquez sur **OK**.

## <a name="next-steps"></a>Étapes suivantes

La page de démarrage de Visual Studio contient désormais un onglet qui affiche un onglet de navigateur Web et un onglet MyButton. Vous pouvez créer des pages de démarrage personnalisées qui ont d’autres fonctionnalités en utilisant le modèle *code-behind* pour ajouter un fichier. dll personnalisé, comme indiqué dans [Ajout d’un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md). Vous pouvez partager des pages de démarrage personnalisées avec d’autres utilisateurs en publiant le fichier. vsix résultant sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou sur un autre site Web ou partage réseau. Pour plus d’informations, consultez [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Voir aussi

- [Personnaliser la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)
- [Contrôles de conteneur WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
