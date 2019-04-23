---
title: UX Essentials pour Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 063818aa828305eedfc184231f2dc4de4eec981c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667453"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials pour Visual Studio
## <a name="best-practices"></a>meilleures pratiques recommandées.

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Soyez cohérent dans l’environnement Visual Studio.

-   Suivez existant [modèles d’interaction](interaction-patterns-for-visual-studio.md) au sein de l’interpréteur de commandes.

-   Conception de fonctionnalités pour être cohérent avec le langage visual de l’interpréteur de commandes et [les exigences de savoir-faire](evaluation-tools-for-visual-studio.md).

-   Utiliser des contrôles et des commandes partagées quand ils existent.

-   Comprendre la hiérarchie de Visual Studio et comment il établit le contexte et les lecteurs de l’interface utilisateur.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utiliser le service de l’environnement pour les polices et couleurs.

-   L’interface utilisateur doit respecter actuel [police d’environnement](fonts-and-formatting-for-visual-studio.md) définition, sauf si elle est exposée pour la personnalisation dans la page polices et couleurs dans la boîte de dialogue Options.

-   Éléments d’interface utilisateur doivent utiliser le [VSColor Service](colors-and-styling-for-visual-studio.md), à l’aide de partagé des jetons d’environnement ou les jetons spécifiques à la fonctionnalité.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Vérifiez toutes les images cohérentes avec le nouveau style de Visual Studio.

-   Suivez les principes de conception de Visual Studio pour les icônes, les glyphes et les autres graphiques.

-   Ne placez pas de texte dans des éléments graphiques.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Conception du point de vue centré sur l’utilisateur.

-   Créer le flux de tâches avant les composants individuels qu’il contient.

-   Vous familiariser avec vos utilisateurs et rendre cette connaissance explicite dans votre spécification.

-   Lors de la révision de l’interface utilisateur, évaluer l’expérience terminée, ainsi que les détails.

-   Concevoir votre interface utilisateur afin qu’il reste fonctionnel et attrayants, quel que soit les paramètres régionaux ou linguistiques.

## <a name="screen-resolution"></a>Résolution d’écran

### <a name="minimum-resolution"></a>Résolution minimale
 - La résolution minimale de Visual Studio Dev14 est **1280 x 720**. Cela signifie qu’il s’agit *possible* à utiliser Visual Studio à cette résolution, bien qu’il ne peut pas être une expérience utilisateur optimale. Il n’existe aucune garantie que tous les aspects seront utilisables à une résolution inférieure à 1280 x 720.

 - La résolution de cible pour Visual Studio est **1366 x 768**. Il s’agit la résolution la plus basse à laquelle nous vous assurons un *bonne* l’expérience utilisateur.

 - Hauteur de la boîte de dialogue initiale doit être **inférieure à 700 pixels**, afin qu’il tienne dans la résolution minimale de l’image de l’IDE à 96 PPP.

### <a name="high-density-displays"></a>Affiche à haute densité
 L’interface utilisateur dans Visual Studio doit fonctionner correctement dans tous les facteurs d’échelle PPP prenant en charge Windows prêt à l’emploi : 150 %, 200 % et 250 %.

## <a name="anti-patterns"></a>Les anti-modèles
 Visual Studio contient de nombreux exemples qui suivent nos instructions et les meilleures pratiques de l’interface utilisateur. Dans le but d’être cohérente, les développeurs emprunt souvent à partir de modèles de conception de l’interface utilisateur produit similaires à ce que leur création. Bien qu’il s’agit d’une bonne approche que vous aide à nous promotion de la cohérence dans l’interaction de l’utilisateur et de conception visuelle, nous parfois livrez fonctionnalités avec quelques informations qui n’a pas été respecté nos instructions en raison des contraintes de planification ou annuler l’inscription de hiérarchisation. Dans ce cas, nous ne voulons pas aux équipes de copier l’une de ces « anti-modèles », car ils prolifèrent incorrect ou incohérent de l’interface utilisateur dans l’environnement Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Champs/paramètres requis indiqués dans l’état d’erreur par défaut

#### <a name="feature-team-goals"></a>Objectifs d’équipe de fonctionnalité

-   Avertir les utilisateurs qu’ils ont ajoutés à un élément qui doit être configuré.

-   Attirer l’attention de l’utilisateur sur les domaines nécessitant une entrée.

#### <a name="anti-pattern-solution"></a>Anti-modèle de solution
 Dès que l’utilisateur a lancé une action et avant qu’ils ont terminé la tâche, placez immédiatement arrêt critique icônes en regard des zones qui nécessitent une configuration.

#### <a name="example-manifest-designer-declarations"></a>Exemple : Déclarations de concepteur du manifeste
 Ajout d’une déclaration à la liste immédiatement le place dans un état d’erreur persiste jusqu'à ce que l’utilisateur définit les propriétés requises.

 Dans ce cas, il est une préoccupation supplémentaire, car l’icône utilisée pour l’alerte contient un «&times;« icône, l’icône de suppression commun ne peut pas être utilisée en regard de celle-ci. Par conséquent, l’interface utilisateur utilise un bouton Supprimer, un contrôle plus bringuebalant.

 ![Placer l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle de Visual Studio. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-modèle")<br />Placer l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle de Visual Studio.

#### <a name="alternatives"></a>Alternatives
 Une bien meilleure solution à ce problème consisterait à :

-   Autoriser l’utilisateur à ajouter une déclaration sans avertissement et d’accéder immédiatement à définir des propriétés sur l’élément.

-   Ajouter l’icône d’avertissement (triangle gold) lorsque le focus se déplace à partir de l’élément, par exemple pour ajouter une autre déclaration à la liste ou tentent de modifier des onglets dans le concepteur.

-   Si l’utilisateur tente de remplacer les tabulations avant de définir des propriétés sur toutes les déclarations, affiche une boîte de dialogue expliquant que l’application n’est pas générée (ou toutes les implications) jusqu'à ce que les avertissements sont résolus. Si l’utilisateur ferme la boîte de dialogue et remplace les tabulations quand même une icône (critique ou avertissement, le cas échéant) est ajoutée à l’onglet déclarations.

### <a name="multiple-clicks-to-dismiss-ui"></a>Plusieurs clics pour fermer l’interface utilisateur

#### <a name="feature-team-goals"></a>Objectifs d’équipe de fonctionnalité
 Ne pas autoriser l’utilisateur ferme l’interface utilisateur sans premier voir le texte d’explication.

#### <a name="anti-pattern"></a>Anti-modèle
 L’équipe insertion les liens vidéo dans plusieurs endroits de l’interface utilisateur de Visual Studio a décidé par rapport au modèle commun de la «&times;« explication ferme de bouton et info-bulle comme spécifié par l’expérience utilisateur, implémenté à la place d’une liste déroulante et « Ne plus afficher » lier.

#### <a name="example-video-links-in-team-explorer"></a>Exemple : les liens vidéo dans Team Explorer
Forcer l’utilisateur à lire le texte explicatif avant de faire disparaître de l’interface utilisateur est un anti-modèle dans Visual Studio. Liens correctement conçues, la vidéo doivent afficher une info-bulle avec des informations supplémentaires sur le pointage et en cliquant sur le «&times;» devrait faire disparaître le message sans avoir besoin d’interagir avec.

 ![Texte explicatif anti&#45;modèle &#45; incorrect](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Modèle de lien vidéo incorrect

#### <a name="result"></a>Résultat
 Au lieu d’un bouton Fermer simple (un seul clic), l’utilisateur est obligé d’utiliser les deux clics pour ignorez simplement l’interface utilisateur dans chaque endroit apparaissant dans les liens vidéo.

#### <a name="alternatives"></a>Alternatives
 La conception correcte pour cette situation serait de suivre le modèle commun pour Internet Explorer, Office et Visual Studio : quand vous placez, l’utilisateur peut voir la description de l’info-bulle et un seul clic masque l’interface utilisateur.

 ![Texte explicatif anti&#45;modèle &#45; correct](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti modèle correctes")<br />Modèle de lien vidéo correct

### <a name="using-command-bars-for-settings"></a>À l’aide des barres de commandes pour les paramètres
 **Figure A** représente cette anti-modèle : placer un paramètre en dessous d’un bouton de commande qui s’applique à plus que la commande. Dans cette ébauche, il existe des commandes en plus de démarrer le débogage, comme l’affichage dans le navigateur, démarrer sans débogage et pas à pas détaillé, qui respecte le paramètre sélectionné.

  ![Figure a : Anti-modèle de barre de commandes](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-modèle-FigureA")<br />Figure a : Anti-modèle de barre de commandes

 Indésirable légèrement meilleur, mais toujours, placer les paramètres de ce type dans les barres d’outils, comme indiqué dans **Figure B**. Bien que les boutons partagés prennent moins d’espace et sont par conséquent une amélioration sur les listes déroulantes, ces deux conceptions utilisent toujours une barre d’outils pour promouvoir un élément qui n’est pas vraiment une commande.

 ![Figure b : Mieux, mais toujours un anti-modèle de barre de commandes](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-modèle-FigureB")<br />Figure b : Mieux, mais toujours un anti-modèle de barre de commandes

  Dans l’approche correcte illustrée **Figure C**, le paramètre est lié à une série de commandes. Il n’existe aucun paramètre global défini et nous allons simplement basculer entre quatre commandes. Il s’agit de la seule situation dans laquelle les commandes dans la barre d’outils sont acceptables.

 ![Figure c : Corriger l’utilisation du modèle de barre de commandes de Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-modèle-FigureC")<br />Figure c : Utilisation correcte du modèle de barre de commandes Visual Studio

### <a name="control-anti-patterns"></a>Anti-modèles de contrôle
 Quelques anti-modèles sont utilisation simplement incorrecte ou une présentation d’un contrôle ou un groupe de contrôles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Soulignement utilisé comme étiquette de groupe, pas un lien hypertexte
 Souligner le texte doit être utilisé uniquement pour les liens hypertexte.

 **Défectueux :** ![Texte souligné qui n’est pas un lien hypertexte est un anti-modèle de Visual Studio. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Texte souligné qui n’est pas un lien hypertexte est un anti-modèle de Visual Studio.

 **Bon :** ![Style correct, non-lien hypertexte s’affiche sans ornement dans la police d’environnement. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Style correct, non-lien hypertexte s’affiche sans ornement dans la police d’environnement.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>En cliquant sur une case à cocher des résultats dans une boîte de dialogue contextuelle
 Cliquer immédiatement sur la case à cocher « Activer le Bureau à distance pour tous les rôles » dans l’Assistant « Publication d’Application Windows Azure » pour afficher une boîte de dialogue contextuelle, un anti-modèle de Visual Studio. En outre, le champ de case à cocher ne remplit pas avec une case à cocher après avoir été sélectionné, un autre anti-modèle interaction.

 ![Afficher une boîte de dialogue une fois en cliquant sur une case à cocher est un anti-modèle de Visual Studio. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Afficher une boîte de dialogue une fois en cliquant sur une case à cocher est un anti-modèle de Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Anti-modèles de lien hypertexte
 L’exemple suivant contient deux anti-modèles.

1. Premier plan sous tension rouge pointage signifie que la couleur appropriée partagée à partir du service de la police n’est pas utilisée.

2. « En savoir plus » n’est pas le texte approprié pour un lien vers une rubrique conceptuelle. L’utilisateur vise ne pas à en savoir plus, qu'il est de comprendre les conséquences de leur choix.

   ![En ignorant le service de couleur et à l’aide de « En savoir plus » pour les liens hypertexte sont anti-modèles de Visual Studio. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />En ignorant le service de couleur et à l’aide de « En savoir plus » pour les liens hypertexte sont anti-modèles de Visual Studio.

   **Meilleure solution :** Poser la question de que l’utilisateur serait demanderez en cliquant sur le lien.

-   Fonctionnement des services Windows Azure

-   Lorsque j’ai besoin d’un projet Windows Azure Mobile Services ?

#### <a name="using-click-here-for-links"></a>À l’aide de « Cliquez ici » pour obtenir des liens
 Des liens hypertexte doivent être autodescriptives. Il est un anti-modèle à utiliser « Cliquez ici » ou toute variante similaire.

 **Défectueux :** « Cliquez ici pour obtenir des instructions sur la création d’un nouveau projet. »

 **Bon :** « Comment créer un nouveau projet ? »