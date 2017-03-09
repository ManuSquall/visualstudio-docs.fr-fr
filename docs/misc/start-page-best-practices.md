---
title: "Bonnes pratiques pour la page de d&#233;marrage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conseils pour la page de démarrage"
  - "bonnes pratiques pour la page de démarrage"
  - "conception de page de démarrage"
ms.assetid: f6ce1ce0-746e-4004-a37f-6f176f6f5851
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Bonnes pratiques pour la page de d&#233;marrage
Étant donné que la page de démarrage peut accéder aux commandes de Visual Studio et qu’elle s’affiche à chaque chargement de Visual Studio, nous vous recommandons de vous assurer de la stabilité des pages de démarrage personnalisées avant de les utiliser ou de les distribuer. Cette rubrique présente les bonnes pratiques pour concevoir des pages de démarrage robustes et explique comment créer une interface utilisateur utile.  
  
## Recommandations en matière de stabilité  
  
### Disponibilité des ressources  
 Pour qu’une page de démarrage personnalisée soit robuste, l’essentiel consiste à s’assurer que toutes les ressources sont disponibles :  
  
-   Tous les packages nécessaires sont installés.  
  
-   Les packages sont préchargés.  
  
-   Tous les assemblys nécessaires se trouvent dans le dossier \\PrivateAssemblies\\.  
  
-   Chaque composant qui utilise une connexion réseau ou Internet dispose d’autres chemins pour les scénarios hors connexion et les connexions interrompues.  
  
### Performances  
 Si votre page de démarrage a d’importants besoins en mémoire ou charge de nombreuses ressources, étudiez comment les performances de démarrage peuvent être affectées. Programmez ces pages de démarrage pour qu’elles chargent les composants à la demande ou en arrière\-plan si cela est possible, pour que le temps de démarrage n’augmente pas de manière significative.  
  
### Processus de développement  
 Si vous modifiez directement la page de démarrage active, vous risquez d’introduire par inadvertance des erreurs qui provoquent le blocage de Visual Studio. Étant donné que la page de démarrage s’ouvre chaque fois que Visual Studio s’ouvre, un blocage de page de démarrage est difficile à corriger. Nous vous recommandons de modifier des copies des fichiers de page de démarrage et de tester leur fiabilité dans une instance expérimentale de Visual Studio. Une fois la nouvelle page de démarrage stable, vous pouvez la configurer pour qu’elle s’exécute dans l’instance principale de Visual Studio.  
  
> [!NOTE]
>  Nous vous recommandons également de tester toute page de démarrage tierce dans une instance expérimentale de Visual Studio avant de l’utiliser dans l’instance principale.  
  
##### Pour tester une page de démarrage dans une instance expérimentale de Visual Studio  
  
1.  Si vous utilisez le modèle de projet de page de démarrage, appuyez sur F5. Sinon :  
  
    1.  Copiez le fichier .xaml et tout le texte ou le balisage de prise en charge dans \\%USERPROFILE%\\My Documents\\Visual Studio *\<version\>*\\StartPages\\.  
  
    2.  Copiez tous les assemblys nécessaires dans *\<chemin\_d’installation\_de\_Visual Studio\>*\\Common7\\IDE\\PrivateAssemblies\\.  
  
    3.  Ouvrez une instance expérimentale de Visual Studio en exécutant la commande suivante à une invite de commandes de Visual Studio.  
  
         **Devenv \/rootsuffix exp**  
  
2.  Dans le menu **Outils**, cliquez sur **Options**. Sélectionnez **Environnement**, puis **Démarrage**. Dans la liste **Personnaliser la page de démarrage**, sélectionnez le fichier StartPage.xaml renommé et cliquez sur **OK**.  
  
3.  Dans le menu **Affichage**, cliquez sur **Page de démarrage**.  
  
     La page de démarrage personnalisée s’ouvre. Si la page de démarrage que vous modifiez se bloque, vous pouvez redémarrer l’instance principale de Visual Studio, effectuer les corrections nécessaires, puis ouvrir une autre instance expérimentale pour pouvoir continuer à modifier votre page de démarrage personnalisée.  
  
 Si votre page de démarrage provoque le blocage de l’instance principale de Visual Studio, vous pouvez désactiver temporairement les pages de démarrage personnalisées en affectant la valeur 0 à la valeur de Registre HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\CustomizationEnabled. Vous pouvez aussi renommer temporairement le fichier .xaml de votre page de démarrage par défaut actuelle. Ces deux approches vous permettent d’ouvrir Visual Studio suffisamment longtemps pour corriger l’erreur.  
  
### Débogage  
 La fenêtre d’outils de page de démarrage intercepte les exceptions lors du chargement initial d’une page de démarrage, mais elle n’intercepte pas les exceptions après cela. Vous pouvez faire en sorte que Visual Studio affiche toutes les exceptions non gérées en affectant la valeur « 1 » à la valeur de Registre suivante.  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\General\\EnableUnhandledExceptionDisplay  
  
 Les informations sur l’exception sont affichées dans une boîte de message, ce qui vous permet de déboguer les contrôles dans une page de démarrage ou à d’autres emplacements non gérés, même dans l’instance principale de Visual Studio. Si vous ne pouvez pas déboguer une fois l’exception levée, vous pouvez redémarrer Visual Studio avec la commande « devenv \/safemode », revenir à votre page de démarrage précédente, puis continuer le débogage dans l’instance expérimentale.  
  
### Chemins relatifs  
 Quand vous faites référence à des chemins de fichier à partir d’une page de démarrage, vous devez toujours utiliser un chemin relatif pour que différentes configurations système soient possibles. Toutefois, la racine de tous les chemins relatifs dans une page de démarrage ne résout pas le dossier \\StartPages\\, mais ..\\*dossier\_installation\_Visual Studio*\\Common7\\IDE, où se trouve devenv.exe. Pour définir un chemin relatif vers le dossier \\StartPages\\, utilisez le convertisseur relatif de page de démarrage VS. Pour cela, affectez la valeur `vs:StartPageRelative` à la propriété `Source` de l’objet, comme illustré dans l’exemple suivant.  
  
 XAML  
  
```  
<Image Source="{vs:StartPageRelative myImage.png}" .../>  
```  
  
 Utilisez la syntaxe de chemin relatif standard lors de l’accès aux ressources fournies avec Visual Studio ou aux fichiers fournis avec d’autres packages.  
  
### Déploiement  
 Nous recommandons d’adopter les bonnes pratiques suivantes quand vous distribuez une page de démarrage personnalisée à d’autres utilisateurs.  
  
#### Paramètres utilisateur  
  
-   Respectez les paramètres utilisateur. Ne remplacez pas les préférences de page de démarrage existantes.  
  
#### VSIX  
 Les pratiques suivantes s’appliquent au déploiement VSIX :  
  
-   Utilisez l’élément [GettingStartedGuide](http://msdn.microsoft.com/fr-fr/261bb1fd-abae-4ed6-80a8-90d5fc3bb8c6) dans le manifeste VSIX pour pointer vers des instructions expliquant comment définir la page de démarrage par défaut.  
  
-   Utilisez les éléments [Name](http://msdn.microsoft.com/fr-fr/d99d38d1-060b-401a-9b9f-ede2c6213a11) et [Description](http://msdn.microsoft.com/fr-fr/24ddc57e-e991-4a43-b0c9-0e76da293e99) du manifeste VSIX pour identifier clairement l’extension comme page de démarrage et pour décrire sa fonction.  
  
-   Vérifiez que votre manifeste VSIX ne contient pas de chemins absolus.  
  
-   Quand vous effectuez le chargement sur le site web de la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), incluez un balisage approprié pour que les utilisateurs puissent identifier l’extension comme une page de démarrage.  
  
#### MSI  
 Si vous générez une page de démarrage dans le cadre d’une extension plus large que vous déployez dans un package Windows Installer \(MSI\), vous pouvez configurer la page de démarrage pour qu’elle soit installée comme page de démarrage par défaut sur l’ordinateur cible. Pour ce faire, écrivez le nom du fichier .xaml de la page de démarrage comme valeur d’URI de la clé de Registre suivante : HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\. Suivez les instructions ci\-dessous quand vous définissez cette valeur de Registre :  
  
-   Dans le programme d’installation, fournissez une interface utilisateur pour que l’utilisateur puisse faire de la nouvelle page de démarrage la page de démarrage par défaut.  
  
-   Si l’utilisateur désinstalle votre extension, rétablissez la valeur de Registre précédente.  
  
### Windows Presentation Framework \(WPF\)  
 Votre balisage XAML doit respecter les bonnes pratiques WPF. Pour plus d’informations sur les bonnes pratiques [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] et [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] pour le développement d’applications, consultez les rubriques suivantes, selon le cas.  
  
|Zone|Rubrique|  
|----------|--------------|  
|Accessibilité|[Accessibility Best Practices](../Topic/Accessibility%20Best%20Practices.md)|  
|Localisation|[Vue d’ensemble de la globalisation et de la localisation WPF](../Topic/WPF%20Globalization%20and%20Localization%20Overview.md)|  
|Performances|[Optimisation des performances des applications WPF](../Topic/Optimizing%20WPF%20Application%20Performance.md)|  
|Sécurité|[Sécurité \(WPF\)](../Topic/Security%20\(WPF\).md)|  
  
## Recommandations en matière d’interface utilisateur  
 Pour garantir une expérience utilisateur conviviale et intuitive sur votre page de démarrage, respectez les recommandations suivantes en matière d’interface utilisateur, le cas échéant.  
  
### Ligne du haut  
  
#### Bannière  
  
-   Faites en sorte que la hauteur de l’image de bannière soit identique à la hauteur de la définition de ligne de la ligne qui la contient.  
  
-   Pour prendre en charge différentes tailles de fenêtre et résolutions d’écran, faites en sorte que l’image de bannière soit agréable à l’œil quelle que soit la largeur.  
  
-   Ne surchargez pas la bannière. Ne superposez pas de boutons ou graphiques supplémentaires sur le logo.  
  
### Colonne de gauche  
  
#### Zone de bouton  
  
-   Placez uniquement les contrôles les plus couramment utilisés dans la zone de bouton pour que les noms des projets récents puissent être affichés. Nous vous recommandons d’afficher moins de cinq boutons.  
  
#### Projets récents  
  
-   Ce contrôle permet à l’utilisateur d’accéder aux projets récents. Vous pouvez afficher de 0 à 24 projets. Comme il s’agit de la section de la page de démarrage la plus fréquemment utilisée, nous vous recommandons de ne pas la supprimer.  
  
#### Options de la page de démarrage  
  
-   Vérifiez que les options **Fermer la page après le chargement du projet** et **Afficher la page de démarrage** sont affichées dans la page de démarrage.  
  
-   Pour les autres contrôles de cette zone, nous vous recommandons d’utiliser des cases à cocher ou des cases d’option, et de vous assurer que les contrôles sont liés aux préférences de la page de démarrage.  
  
### Zone de contenu  
  
#### Onglets de niveau supérieur  
  
-   Évitez d’ajouter trop d’onglets pour ne pas que le contrôle Onglet soit renvoyé à la ligne dans les largeurs d’écran classiques.  
  
-   Utilisez des noms courts et descriptifs pour les onglets.  
  
-   Vérifiez que les onglets représentent des zones de contenu groupées.  
  
#### Onglets de niveau inférieur  
  
-   Utilisez la navigation de niveau inférieur uniquement si vous avez plus de deux sous\-rubriques.  
  
-   Évitez d’ajouter trop d’onglets pour ne pas que le contrôle Onglet soit renvoyé à la ligne dans les largeurs d’écran classiques.  
  
-   Utilisez des noms courts et descriptifs pour les onglets.  
  
#### Contenu des onglets de niveau inférieur  
  
-   N’affichez pas plus de cinq éléments de contenu sous un onglet de niveau inférieur.  
  
#### Contenu des éléments  
  
-   N’affichez pas plus de quatre liens par élément de contenu.  
  
-   Si vous associez des images à des éléments de contenu, vérifiez que chaque image fait 175 x 125 pixels.  
  
-   Utilisez des titres courts et descriptifs pour les éléments de contenu.  
  
-   Limitez les descriptions des éléments de contenu à une ou deux phrases.  
  
### Général  
  
#### Animations  
  
-   Si vous utilisez des animations, limitez\-les à 0,5 seconde ou moins pour empêcher de percevoir de mauvaises performances.  
  
#### Couleurs de l’environnement  
  
-   Respectez les paramètres système pour les polices et les couleurs.  
  
-   Utilisez des arrière\-plans de couleur claire.  
  
-   Utilisez la détection de bureau à distance pour garantir une dégradation des couleurs correcte dans les sessions à distance.  
  
## Voir aussi  
 [Architecture de la page de démarrage](/visual-cpp/misc/start-page-architecture)   
 [Déploiement de Pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md)   
 [Ajout de commandes de Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)