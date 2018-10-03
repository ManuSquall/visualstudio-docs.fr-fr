---
title: Créer votre propre Page de démarrage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: douge
ms.openlocfilehash: 87195c318f6bdc04dc0cfde54c35577142661224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493204"
---
# <a name="creating-your-own-start-page"></a>Création de votre propre page de démarrage
Vous pouvez créer une page de démarrage personnalisée en utilisant le modèle de projet Page de démarrage ou en créant une page de démarrage vierge.  
  
 Le concepteur XAML ne peut pas fournir des représentations visuelles entièrement exactes des pages de démarrage personnalisées en raison des dépendances au modèle d’application Visual Studio.  
  
## <a name="using-the-project-template"></a>Utilisation du modèle de projet  
 Le modèle de projet Page de démarrage crée un projet Page de démarrage qui est une copie intégrale de la page de démarrage de Visual Studio. Vous pouvez ensuite modifier la page de démarrage en appliquant vos spécifications.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Pour créer une page de démarrage personnalisée à l’aide du modèle de projet Page de démarrage  
  
1.  Téléchargez et installez le [modèle de projet Page de démarrage](http://go.microsoft.com/fwlink/?LinkId=186204) à partir de la galerie Visual Studio.  
  
    > [!WARNING]
    >  À l’heure actuelle, le modèle de projet Page de démarrage Visual Studio 2010 n’a pas encore été mis à jour. Pour plus d’informations sur la mise à niveau de ce modèle, consultez [Comment : mettre à niveau une Page de démarrage de Visual Studio personnalisé](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Une fois que vous avez installé le modèle, utilisez-le pour créer une nouvelle page de démarrage.  
  
3.  Dans le volet gauche de la boîte de dialogue Nouveau projet, sous **Modèles installés**, développez le nœud **Autres types de projets** , puis cliquez sur **Extensibilité**.  
  
4.  Dans le volet central, cliquez sur **Page de démarrage personnalisée**, puis nommez votre projet et cliquez sur **OK**.  
  
     Visual Studio crée un projet Page de démarrage qui est une copie intégrale de la page de démarrage de Visual Studio.  
  
5.  Dans l’ **Explorateur de solutions**, ouvrez **StartPage.xaml**.  
  
6.  Modifiez StartPage.xaml.  
  
     Vous pouvez afficher votre travail en appuyant sur F5 pour ouvrir une instance expérimentale de Visual Studio à l’aide de la page de démarrage personnalisée installée.  
  
## <a name="creating-a-blank-start-page"></a>Création d’une page de démarrage vierge  
 Pour créer une page de démarrage vierge, le plus simple est d’utiliser le modèle de projet Page de démarrage, puis d’en supprimer le contenu.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Pour créer une page de démarrage vierge à l’aide du modèle de projet Page de démarrage  
  
1.  Créez un projet de page de démarrage en utilisant le modèle de projet Page de démarrage, comme décrit dans la procédure précédente.  
  
2.  Ouvrez StartPage.xaml.  
  
3.  Supprimer tout le contenu de la page, en laissant uniquement les éléments xml externe et la grille contenante <xref:System.Windows.Controls.Grid> élément, afin que votre fichier .xaml ressemble à l’exemple suivant.  
  
    ```xaml
       <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                 xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                 xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                 xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
             mc:Ignorable="d" 
                 d:DesignHeight="600" d:DesignWidth="800">
        <Grid>
            <!--Add content here.-->
        </Grid>
    </Grid>
    ```
      
4.  Supprimez les fichiers de prise en charge que vous ne comptez pas utiliser.  
  
     Vous devez conserver les fichiers .vsix et .pkgdef pour le déploiement.  
  
 Vous pouvez également créer une page de démarrage vierge en créant un fichier XAML avec la structure de balise nécessaire pour qu’il soit reconnu par Visual Studio. Vous pouvez ensuite ajouter des balises et le code-behind pour obtenir l’apparence et les fonctionnalités voulues. Pour plus d’informations, consultez [création d’une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Test et application de la page de démarrage personnalisée  
 Ne définissez pas l’instance principale de manière à exécuter la page de démarrage personnalisée avant de vérifier qu’elle ne se bloque pas. Quand vous avez testé votre page de démarrage personnalisée, vous pouvez l’appliquer à votre système en répétant les trois dernières étapes de cette procédure dans l’instance principale de Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Pour afficher une page de démarrage personnalisée  
  
1.  Appuyez sur F5.  
  
     L’instance expérimentale de Visual Studio s’ouvre avec la nouvelle page de démarrage installée, mais non sélectionnée.  
  
2.  Dans l’instance expérimentale de Visual Studio, dans le menu **Outils** , cliquez sur **Options**.  
  
3.  Dans la boîte de dialogue **Options** , sous **Environnement**, sélectionnez **Démarrage**. Ensuite, dans la liste **Personnaliser la page de démarrage** , sélectionnez le fichier .xaml, puis cliquez sur **OK**.  
  
4.  Dans le menu **Affichage** , cliquez sur **Page de démarrage**.  
  
     La page de démarrage active s’affiche. Vous devez fermer l’instance expérimentale, recopier les fichiers modifiés, puis rouvrir l’instance expérimentale pour voir les modifications.  
  
 Vous pouvez partager votre page de démarrage personnalisée en chargeant le fichier .vsix depuis votre répertoire bin\debug vers le site web de la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) ou vers un autre site web ou intranet de partage. Pour plus d’informations, consultez [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de la Page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Procédure pas à pas : Ajout de code XAML personnalisé à la page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)