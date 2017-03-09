---
title: "Cr&#233;ation de votre propre page de d&#233;marrage | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Créer la page de démarrage"
  - "page de démarrage personnalisée"
  - "personnaliser la page de démarrage"
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Cr&#233;ation de votre propre page de d&#233;marrage
Vous pouvez créer une page de démarrage personnalisée en utilisant le modèle de projet Page de démarrage ou en créant une page de démarrage vierge.  
  
 Le concepteur XAML ne peut pas fournir des représentations visuelles entièrement exactes des pages de démarrage personnalisées en raison des dépendances au modèle d’application Visual Studio.  
  
## Utilisation du modèle de projet  
 Le modèle de projet Page de démarrage crée un projet Page de démarrage qui est une copie intégrale de la page de démarrage de Visual Studio. Vous pouvez ensuite modifier la page de démarrage en appliquant vos spécifications.  
  
#### Pour créer une page de démarrage personnalisée à l’aide du modèle de projet Page de démarrage  
  
1.  Téléchargez et installez le [modèle de projet Page de démarrage](http://go.microsoft.com/fwlink/?LinkId=186204) à partir de la galerie Visual Studio.  
  
    > [!WARNING]
    >  À l’heure actuelle, le modèle de projet Page de démarrage Visual Studio 2010 n’a pas encore été mis à jour. Pour plus d’informations sur la mise à niveau de ce modèle, consultez [Procédure : mise à niveau d’une page de démarrage personnalisée Visual Studio](../Topic/How%20to:%20Upgrade%20a%20Visual%20Studio%20Custom%20Start%20Page.md).  
  
2.  Une fois que vous avez installé le modèle, utilisez\-le pour créer une nouvelle page de démarrage.  
  
3.  Dans le volet gauche de la boîte de dialogue Nouveau projet, sous **Modèles installés**, développez le nœud **Autres types de projets**, puis cliquez sur **Extensibilité**.  
  
4.  Dans le volet central, cliquez sur **Page de démarrage personnalisée**, puis nommez votre projet et cliquez sur **OK**.  
  
     Visual Studio crée un projet Page de démarrage qui est une copie intégrale de la page de démarrage de Visual Studio.  
  
5.  Dans l’**Explorateur de solutions**, ouvrez **StartPage.xaml**.  
  
6.  Modifiez StartPage.xaml.  
  
     Vous pouvez afficher votre travail en appuyant sur F5 pour ouvrir une instance expérimentale de Visual Studio à l’aide de la page de démarrage personnalisée installée.  
  
## Création d’une page de démarrage vierge  
 Pour créer une page de démarrage vierge, le plus simple est d’utiliser le modèle de projet Page de démarrage, puis d’en supprimer le contenu.  
  
#### Pour créer une page de démarrage vierge à l’aide du modèle de projet Page de démarrage  
  
1.  Créez un projet de page de démarrage en utilisant le modèle de projet Page de démarrage, comme décrit dans la procédure précédente.  
  
2.  Ouvrez StartPage.xaml.  
  
3.  Supprimez le contenu de la page, en laissant uniquement les éléments xml externes et l’élément <xref:System.Windows.Controls.Grid> de la grille contenante, pour que le fichier .xaml ressemble à l’exemple suivant.  
  
     [!code-xml[BlankStartPage#01](../misc/codesnippet/Xaml/creating-your-own-start-page_1.xaml)]  
  
4.  Supprimez les fichiers de prise en charge que vous ne comptez pas utiliser.  
  
     Vous devez conserver les fichiers .vsix et .pkgdef pour le déploiement.  
  
 Vous pouvez également créer une page de démarrage vierge en créant un fichier XAML avec la structure de balise nécessaire pour qu’il soit reconnu par Visual Studio. Vous pouvez ensuite ajouter des balises et le code\-behind pour obtenir l’apparence et les fonctionnalités voulues. Pour plus d’informations, consultez [Création d'une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).  
  
## Test et application de la page de démarrage personnalisée  
 Ne définissez pas l’instance principale de manière à exécuter la page de démarrage personnalisée avant de vérifier qu’elle ne se bloque pas. Quand vous avez testé votre page de démarrage personnalisée, vous pouvez l’appliquer à votre système en répétant les trois dernières étapes de cette procédure dans l’instance principale de Visual Studio.  
  
#### Pour afficher une page de démarrage personnalisée  
  
1.  Appuyez sur F5.  
  
     L’instance expérimentale de Visual Studio s’ouvre avec la nouvelle page de démarrage installée, mais non sélectionnée.  
  
2.  Dans l’instance expérimentale de Visual Studio, dans le menu **Outils**, cliquez sur **Options**.  
  
3.  Dans la boîte de dialogue **Options**, sous **Environnement**, sélectionnez **Démarrage**. Ensuite, dans la liste **Personnaliser la page de démarrage**, sélectionnez le fichier .xaml, puis cliquez sur **OK**.  
  
4.  Dans le menu **Affichage**, cliquez sur **Page de démarrage**.  
  
     La page de démarrage active s’affiche. Vous devez fermer l’instance expérimentale, recopier les fichiers modifiés, puis rouvrir l’instance expérimentale pour voir les modifications.  
  
 Vous pouvez partager votre page de démarrage personnalisée en chargeant le fichier .vsix depuis votre répertoire bin\\debug vers le site web de la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) ou vers un autre site web ou intranet de partage. Pour plus d’informations, consultez [Déploiement de Pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md).  
  
## Voir aussi  
 [Personnalisation de la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Procédure pas à pas : Ajout de code XAML personnalisé à la Page de démarrage](../Topic/Walkthrough:%20Adding%20Custom%20XAML%20to%20the%20Start%20Page.md)