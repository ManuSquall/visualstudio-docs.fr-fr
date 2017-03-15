---
title: Essentials UX pour Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7f10e2cefc0986a2457cc61945a60acfd1a4ef78
ms.lasthandoff: 02/22/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Essentials UX pour Visual Studio
## <a name="best-practices"></a>meilleures pratiques recommandées.  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Être cohérent dans l’environnement Visual Studio.  
  
-   Suivez les modèles d’interaction existant au sein de l’interpréteur de commandes.  
  
-   Conception de fonctionnalités pour être conforme aux spécifications de langue et de savoir-faire visual du shell.  
  
-   Utilisation des contrôles et des commandes partagés lorsqu’elles existent.  
  
-   Comprendre la hiérarchie de Visual Studio et comment il établit le contexte et les lecteurs de l’interface utilisateur.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utiliser le service de l’environnement pour les polices et couleurs.  
  
-   L’interface utilisateur doit respecter le paramètre de police d’environnement en cours, sauf si elle est exposée pour la personnalisation de la page polices et couleurs dans la boîte de dialogue Options.  
  
-   Éléments d’interface utilisateur doivent utiliser le VSColor Service, à l’aide de jetons de l’environnement partagé ou spécifique à la fonctionnalité.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Rendre toutes les images cohérent avec le nouveau style de Visual Studio.  
  
-   Suivez les principes de conception de Visual Studio pour les icônes, les glyphes et les autres graphiques.  
  
-   Ne placez pas de texte dans des éléments graphiques.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Conception du point de vue centré sur l’utilisateur.  
  
-   Créez le flux de tâches avant les composants individuels qu’il contient.  
  
-   Connaître vos utilisateurs et rendre cette connaissance explicite dans votre spec.  
  
-   Lorsque vous parcourez l’interface utilisateur, évaluer l’expérience complète ainsi que les détails.  
  
-   Concevoir votre interface utilisateur afin qu’il reste fonctionnelle et attractive, quelle que soit la langue ou de paramètres régionaux.  
  
## <a name="screen-resolution"></a>Résolution d’écran  
  
### <a name="minimum-resolution"></a>Résolution minimale  
 La résolution minimale pour Visual Studio Dev14 est 1280 x 1024. Cela signifie qu’il est *possible* pour Visual Studio à cette résolution, bien qu’il ne peut pas être une expérience utilisateur optimale. Il n’existe aucune garantie que tous les aspects sera utilisables à une résolution inférieure à 1280 x 1024.  
  
 Taille de la boîte de dialogue initiale ne doit pas dépasser 1000 pixels de hauteur pour s’ajuster dans le cadre de l’IDE dans cette résolution minimale à 96 PPP.  
  
### <a name="high-density-displays"></a>Affichages haute densités  
 L’interface utilisateur dans Visual Studio doit fonctionner correctement dans PPP tous les facteurs Windows prend en charge l’emploi d’échelle : 150 %, 200 % et 250 %.  
  
## <a name="anti-patterns"></a>Les anti-modèles  
 Visual Studio contient de nombreux exemples de l’interface utilisateur qui suivent nos conseils et les meilleures pratiques. Dans un souci de cohérence, les développeurs emprunt souvent des modèles de conception de l’interface utilisateur produit similaires à ce que leur création. Bien qu’il s’agit d’une bonne approche que vous aide à nous lecteur la cohérence de l’interaction de l’utilisateur et la conception visuelle, nous parfois livrez fonctionnalités avec quelques détails qui n’a pas été respecté nos instructions en raison des contraintes de planification ou annuler l’inscription de hiérarchisation. Dans ce cas, vous ne souhaitez pas les équipes de copier l’un de ces « anti-modèles », car elles prolifèrent incorrect ou incohérent de l’interface utilisateur dans l’environnement Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Champs/paramètres requis indiqués dans l’état d’erreur par défaut  
  
#### <a name="feature-team-goals"></a>Objectifs d’équipe de fonctionnalité  
  
-   Avertir les utilisateurs qu’ils ont ajoutés un élément qui doit être configuré.  
  
-   Attirer l’attention de l’utilisateur sur les points d’entrée.  
  
#### <a name="anti-pattern-solution"></a>Anti-modèle de solution  
 Dès que l’utilisateur a lancé une action et avant qu’ils ont terminé la tâche, placez immédiatement arrêt critique icônes en regard les zones qui nécessitent une configuration.  
  
#### <a name="example-manifest-designer-declarations"></a>Exemple : Déclarations de Concepteur de manifestes  
 Ajout d’une déclaration immédiatement à la liste le place dans un état d’erreur persiste jusqu'à ce que l’utilisateur définit les propriétés requises.  
  
 Dans ce cas, il existe un problème supplémentaire, car l’icône utilisée pour l’alerte contient un « x », afin de supprimer le common icône ne peut pas être utilisée en regard. Par conséquent, l’interface utilisateur utilise un bouton Supprimer, un contrôle plus bringuebalant.  
  
 ![Manifeste concepteur erreur anti-modèle de déclaration](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-modèle")  
  
 **Placement de l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle Visual Studio.**  
  
#### <a name="alternatives"></a>Alternatives  
 Une bien meilleure solution à ce problème consisterait à :  
  
-   Autoriser l’utilisateur à ajouter une déclaration sans avertissement et déplacez immédiatement définir les propriétés sur l’élément.  
  
-   Ajoutez l’icône d’avertissement (triangle gold) lorsque focus se déplace à partir de l’élément, par exemple pour ajouter une autre déclaration à la liste ou tentent de modifier des onglets dans le concepteur.  
  
-   Si l’utilisateur tente de modifier des onglets avant de définir des propriétés sur les déclarations, affiche une boîte de dialogue expliquant que l’application ne sera pas généré (ou toutes les implications) jusqu'à ce que les avertissements sont résolus. Si l’utilisateur ferme la boîte de dialogue et remplace les tabulations quand même une icône (critique ou avertissement, le cas échéant) est ajoutée à l’onglet déclarations.  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Forcer l’utilisateur à lire le texte avant de faire disparaître de l’interface utilisateur  
  
#### <a name="feature-team-goals"></a>Objectifs d’équipe de fonctionnalité  
 Ne pas autoriser l’utilisateur ferme l’interface utilisateur sans premier voir le texte d’explication.  
  
#### <a name="anti-pattern"></a>Anti-modèle  
 L’équipe d’insertion de liens vidéo dans plusieurs endroits de l’interface utilisateur de Visual Studio décidé par rapport au modèle commun de X Fermez explication bouton et info-bulle comme spécifié par l’expérience utilisateur et implémenté à la place une liste déroulante et le lien « Ne plus afficher ».  
  
 ![Anti-modèle texte explicatif : incorrect](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **Incorrect : forcer l’utilisateur à lire le texte explicatif avant de faire disparaître de l’interface utilisateur est un anti-modèle dans Visual Studio.**  
  
#### <a name="result"></a>Résultat  
 Au lieu d’un bouton Fermer simple (un clic), l’utilisateur est obligé d’utiliser deux clics pour simplement ignorer l’interface utilisateur en place pour tous les liens vidéo s’affichent.  
  
#### <a name="alternatives"></a>Alternatives  
 La conception correcte pour cette situation serait de suivre le modèle commun pour Internet Explorer, Office et Visual Studio : survol, l’utilisateur peut voir la description de l’info-bulle et un seul clic masque l’interface utilisateur.  
  
 ![Anti-modèle texte explicatif : correct](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti modèle correctes")  
  
 **Correct : comme prévu, les liaisons vidéo doivent afficher une info-bulle avec des informations supplémentaires pointage et en cliquant sur le « X » doit-elle ignorer le message sans avoir besoin d’interagir avec.**  
  
### <a name="using-command-bars-for-settings"></a>À l’aide des barres de commandes pour les paramètres  
 ![Barre anti-modèle commandes-Figure A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-modèle-FigureA")  
  
 **Figure a : anti-modèle barre de commandes**  
  
 **Figure A** représente cette anti-modèle : placement d’un paramètre en dessous d’un bouton de commande qui s’applique au plus que la commande. Dans cette ébauche, il existe des commandes en plus de démarrer le débogage, comme l’affichage dans le navigateur, démarrer sans débogage et pas à pas détaillé, qui respecte le paramètre sélectionné.  
  
 ![Barre anti-modèle commandes-Figure B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-modèle-FigureB")  
  
 **Figure b : meilleur, mais toujours un anti-modèle de barre de commandes**  
  
 Indésirable légèrement meilleur, mais il existe néanmoins, pour placer les paramètres de ce type dans les barres d’outils, comme indiqué dans **Figure B**. Tandis que les boutons de fractionnement occupent moins de place et sont par conséquent une amélioration sur les listes déroulantes, les deux conceptions utilisent encore une barre d’outils pour promouvoir un élément qui n’est pas vraiment une commande.  
  
 ![Barre anti-modèle commandes-Figure C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-modèle-FigureC")  
  
 **Utilisez figure C: correcte du modèle de barre de commandes de Visual Studio**  
  
 Dans **Figure C**, le paramètre est lié à une série de commandes. Il n’existe aucun paramètre global défini et nous allons simplement passer quatre commandes. Il s’agit du seul cas dans lequel les commandes dans la barre d’outils sont acceptables.  
  
### <a name="control-anti-patterns"></a>Anti-modèles de contrôle  
 Quelques anti-modèles sont simplement mauvaise utilisation ou la présentation d’un contrôle ou d’un groupe de contrôles.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Soulignement utilisé comme étiquette de groupe, pas un lien hypertexte  
 Souligner le texte doit être utilisé uniquement pour les liens hypertexte.  
  
 **Incorrecte :**  
  
 ![Anti-modèle de soulignement dans les étiquettes de groupe](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "g_GroupLabelIncorrect-0102")  
  
 **Texte souligné qui n’est pas un lien hypertexte est un anti-modèle Visual Studio.**  
  
 **Bon :**  
  
 ![Anti-modèle de soulignement dans les étiquettes de groupe (correct)](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "h_GroupLabelCorrect-0102")  
  
 **Style correct, non-lien hypertexte s’affiche sans ornement dans la police d’environnement.**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>En cliquant sur une case à cocher des résultats dans une boîte de dialogue contextuelle  
 Cliquer sur la case à cocher « Activer le Bureau à distance pour tous les rôles » dans l’Assistant « Publier l’Application Windows Azure » immédiatement pour afficher une boîte de dialogue contextuelle, un anti-modèle Visual Studio. En outre, le champ de case à cocher ne remplit pas avec une case à cocher après avoir été sélectionné, un autre anti-modèle interaction.  
  
 ![Anti-modèle contextuel de case à cocher](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "i_CheckboxPopup-0102")  
  
 **Afficher une boîte de dialogue une fois en cliquant sur une case à cocher est un anti-modèle Visual Studio.**  
  
### <a name="hyperlink-anti-patterns"></a>Anti-modèles de lien hypertexte  
 L’exemple suivant contient deux anti-modèles.  
  
1.  Premier plan activation rouge pointage signifie que la couleur appropriée partagée à partir du service de police n’est pas utilisée.  
  
2.  « En savoir plus » n’est pas le texte approprié pour un lien vers une rubrique conceptuelle. L’utilisateur vise ne pas à en savoir plus, qu'il est de comprendre les conséquences de leur choix.  
  
 ![Anti-modèles de lien hypertexte](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "j_HyperlinkIncorrect-0102")  
  
 **En ignorant le service de couleur et à l’aide de « En savoir plus » pour les liens hypertexte sont anti-modèles de Visual Studio.**  
  
 **Une meilleure solution :** poser la question de l’utilisateur serait poser la question en cliquant sur le lien.  
  
-   Fonctionnement des services Windows Azure  
  
-   Quand dois-je un projet Windows Azure Mobile Services ?  
  
#### <a name="using-click-here-for-links"></a>À l’aide de « Cliquez ici » pour obtenir des liens  
 Les liens hypertexte doivent être autodescriptives. Il est un anti-modèle d’utiliser « Cliquez ici » ou des variantes similaires.  
  
 **Mauvais :** « Cliquez ici pour obtenir des instructions sur la création d’un nouveau projet. »  
  
 **Bonne :** « Comment créer un nouveau projet ? »
