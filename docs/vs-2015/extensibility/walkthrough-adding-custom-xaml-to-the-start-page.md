---
title: 'Procédure pas à pas : Ajout de XAML personnalisé à la Page de démarrage | Microsoft Docs'
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
ms.openlocfilehash: 193cea35fb7aa852b996aead6a26fd4e26b7b331
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001666"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Procédure pas à pas : Ajout de code XAML personnalisé à la page de démarrage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer un Visual Studio Page de démarrage personnalisée qui contient un navigateur Web.  
  
## <a name="adding-custom-xaml"></a>Ajout de XAML personnalisé  
  
1.  Créer une Page de démarrage en suivant les instructions dans [création d’une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).  
  
2.  Dans le fichier MainWindow.xaml, recherchez le \<grille > section.  
  
3.  Ajouter un \<TabControl > élément et un \<TabItem > à l’intérieur de la \< grille > élément, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Ajoutez une deuxième \<TabItem >, avec un \<bouton > élément qui ouvre un nouveau projet :  
  
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
  
## <a name="testing-the-custom-start-page"></a>Test de la Page de démarrage personnalisée  
  
1.  Appuyez sur F5.  
  
     L’instance expérimentale de Visual Studio s’ouvre, avec la Page de démarrage personnalisée installée mais ne pas sélectionnée.  
  
2.  Dans l’instance expérimentale de Visual Studio, ouvrez le **Outils /Options / environnement** page.  
  
3.  Sélectionnez **démarrage**. Sur le **personnaliser la Page de démarrage** liste, sélectionnez le fichier .xaml, puis cliquez sur **OK**.  
  
4.  Dans le menu **Affichage** , cliquez sur **Page de démarrage**.  
  
5.  Cliquez sur le **Bing** onglet.  
  
     Vous devez voir une page web de Bing.  
  
6.  Cliquez sur le **MyButton** onglet.  
  
     Vous devez voir un **MonProjet** bouton, ce qui ouvre le **nouveau projet** boîte de dialogue.  
  
7.  Fermez l’instance expérimentale.  
  
## <a name="applying-the-custom-start-page"></a>Application de la Page de démarrage personnalisée  
  
#### <a name="to-test-the-custom-start-page"></a>Pour tester la Page de démarrage personnalisée  
  
1.  Dans **Outils / Options / environnement**, sélectionnez **démarrage**. Sur le **personnaliser la Page de démarrage** liste, sélectionnez le fichier .xaml, puis cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 La Page de démarrage de Visual Studio propose désormais un onglet qui affiche un onglet de navigateur Web et un onglet MyButton. Vous pouvez créer des Pages de démarrage personnalisées qui ont d’autres fonctionnalités à l’aide de la *code-behind* modèle pour ajouter un fichier .dll personnalisé, comme illustré dans [ajouter le contrôle utilisateur à la Page de démarrage](../extensibility/adding-user-control-to-the-start-page.md). Vous pouvez partager des Pages de démarrage personnalisées avec d’autres utilisateurs en publiant le fichier .vsix résultant de la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) site Web, ou vers un autre site Web ou réseau de partage. Pour plus d’informations, consultez [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de la Page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Conteneur des contrôles WPF](http://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
