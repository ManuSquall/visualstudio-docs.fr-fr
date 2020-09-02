---
title: 'Procédure pas à pas : ajout de code XAML personnalisé à la page de démarrage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674123"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Procédure pas à pas : ajout de code XAML personnalisé à la page de démarrage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer une page de démarrage Visual Studio personnalisée qui contient un navigateur Web.  
  
## <a name="adding-custom-xaml"></a>Ajout de code XAML personnalisé  
  
1. Créez une page de démarrage en suivant les instructions fournies dans [création d’une page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).  
  
2. Dans le fichier MainWindow. xaml, recherchez la \<Grid> section.  
  
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
  
## <a name="testing-the-custom-start-page"></a>Test de la page de démarrage personnalisée  
  
1. Appuyez sur F5.  
  
     L’instance expérimentale de Visual Studio s’ouvre, avec la page de démarrage personnalisée installée, mais non sélectionnée.  
  
2. Dans l’instance expérimentale de Visual Studio, ouvrez la page **Outils/Options/environnement** .  
  
3. Sélectionnez **démarrage**. Dans la liste **personnaliser la page de démarrage** , sélectionnez votre fichier. xaml, puis cliquez sur **OK**.  
  
4. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.  
  
5. Cliquez sur l’onglet **Bing** .  
  
     Une page Web Bing doit s’afficher.  
  
6. Cliquez sur l’onglet **MyButton** .  
  
     Vous devez voir un bouton **MyProject** qui ouvre la boîte de dialogue **nouveau projet** .  
  
7. Fermez l’instance expérimentale.  
  
## <a name="applying-the-custom-start-page"></a>Application de la page de démarrage personnalisée  
  
#### <a name="to-test-the-custom-start-page"></a>Pour tester la page de démarrage personnalisée  
  
1. Dans **Outils/Options/environnement**, sélectionnez **démarrage**. Dans la liste **personnaliser la page de démarrage** , sélectionnez votre fichier. xaml, puis cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 La page de démarrage de Visual Studio contient désormais un onglet qui affiche un onglet de navigateur Web et un onglet MyButton. Vous pouvez créer des pages de démarrage personnalisées qui ont d’autres fonctionnalités en utilisant le modèle *code-behind* pour ajouter un fichier. dll personnalisé, comme indiqué dans [Ajout d’un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md). Vous pouvez partager des pages de démarrage personnalisées avec d’autres utilisateurs en publiant le fichier. vsix résultant sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou sur un autre site Web ou partage réseau. Pour plus d’informations, consultez [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Contrôles de conteneur WPF](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
