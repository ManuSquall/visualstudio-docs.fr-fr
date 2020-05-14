---
title: 'Procédure pas à pas : Ajout de XAML personnalisé à la page de départ ( Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697669"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Procédure pas à pas : Ajoutez XAML personnalisé à la page de départ

Ce pas-là montre comment créer une page de démarrage Visual Studio personnalisée qui contient un navigateur Web.

## <a name="add-custom-xaml"></a>Ajouter XAML personnalisé

1. Créez une page de démarrage en suivant les instructions dans [Créer une page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).

2. Dans le fichier *MainWindow.xaml,* trouvez la \<section Grid>.

3. Ajoutez \<un élément TabControl> \<et un TabItem> \< à l’intérieur de l’élément de> grille, comme le montre l’exemple suivant.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Ajoutez un \<deuxième> TabItem, \<avec un élément de> Bouton qui ouvre un nouveau projet :

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

## <a name="test-the-custom-start-page"></a>Testez la page de départ personnalisée

1. Appuyez sur **F5**.

     L’exemple expérimental de Visual Studio s’ouvre, avec la page de démarrage personnalisée installée mais non sélectionnée.

2. Dans l’exemple expérimental de Visual Studio, ouvrez la page **Outils /Options / Environnement.**

3. Sélectionnez **Startup**. Sur la liste De la **page de démarrage personnalisée,** sélectionnez votre fichier *.xaml,* et cliquez **sur OK**.

4. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

5. Cliquez sur l’onglet **Bing.**

     Vous devriez voir une page Web Bing.

6. Cliquez sur l’onglet **MyButton.**

     Vous devriez voir un bouton **MyProject,** qui ouvre le dialogue **du nouveau projet.**

7. Fermez l’instance expérimentale.

Pour appliquer la page de démarrage personnalisée, dans **Tools** > **Options** > **Environment**, sélectionnez **Startup**. Sur la liste De la **page de démarrage personnalisée,** sélectionnez votre fichier *.xaml,* et cliquez **sur OK**.

## <a name="next-steps"></a>Étapes suivantes

La page de démarrage visual Studio contient maintenant un onglet qui affiche un onglet de navigateur Web et un onglet MyButton. Vous pouvez créer des pages de démarrage personnalisées qui ont d’autres fonctionnalités en utilisant le modèle *de code-derrière* pour ajouter un .dll personnalisé, comme indiqué dans [l’ajout de contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md). Vous pouvez partager des pages de démarrage personnalisées avec d’autres utilisateurs en publiant le fichier .vsix résultant sur le site Web [Visual Studio Marketplace,](https://marketplace.visualstudio.com/) ou vers un autre site Web ou partage de réseau. Pour plus d’informations, consultez [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Voir aussi

- [Personnaliser la page de départ](../ide/customizing-the-start-page-for-visual-studio.md)
- [Contrôles des conteneurs WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
