---
title: UX Essentials pour Visual Studio | Microsoft Docs
description: Passez en revue les meilleures pratiques de l’expérience utilisateur pour les nouvelles fonctionnalités que vous développez pour Visual Studio, notamment sur la résolution de l’écran.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74b27e87e6f16130573ef6671286501f77e44352
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899418"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials pour Visual Studio

## <a name="best-practices"></a>Meilleures pratiques

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Soyez cohérent dans l’environnement Visual Studio.

- Suivez les [modèles d’interaction](interaction-patterns-for-visual-studio.md) existants dans le shell.

- Concevez des fonctionnalités cohérentes avec les [exigences en matière](evaluation-tools-for-visual-studio.md)de langage visuel et d’artisan de l’interpréteur de commandes.

- Utilisez des commandes partagées et des contrôles lorsqu’ils existent.

- Comprenez la hiérarchie Visual Studio et comment elle établit le contexte et pilote l’interface utilisateur.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utilisez le service environnement pour les polices et les couleurs.

- L’interface utilisateur doit respecter le paramètre de [police d’environnement](fonts-and-formatting-for-visual-studio.md) actuel, sauf si elle est exposée pour la personnalisation dans la page polices et couleurs de la boîte de dialogue Options.

- Les éléments d’interface utilisateur doivent utiliser le [service VSColor](colors-and-styling-for-visual-studio.md), à l’aide de jetons d’environnement partagés ou de jetons spécifiques aux fonctionnalités.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. faites en sorte que toutes les images soient cohérentes avec le nouveau style VS.

- Suivez les principes de conception de Visual Studio pour les icônes, les glyphes et d’autres graphiques.

- Ne placez pas de texte dans les éléments graphiques.

### <a name="4-design-from-a-user-centric-perspective"></a>4. conception d’une perspective centrée sur l’utilisateur.

- Créez le déroulement des tâches avant les fonctionnalités individuelles qu’il contient.

- Familiarisez-vous avec vos utilisateurs et rendez ces connaissances explicites dans vos spécifications.

- Lorsque vous examinez l’interface utilisateur, évaluez l’expérience complète et les détails.

- Concevez votre interface utilisateur afin qu’elle reste fonctionnelle et attrayante indépendamment des paramètres régionaux ou de la langue.

## <a name="screen-resolution"></a>Résolution de l’écran

### <a name="minimum-resolution"></a>Résolution minimale

- La résolution minimale pour Visual Studio 2015 est **1280 x 720**. Cela signifie qu’il est *possible* d’utiliser Visual Studio à cette résolution, bien qu’il ne s’agisse pas d’une expérience utilisateur optimale. Il n’y a aucune garantie que tous les aspects seront utilisables à des résolutions inférieures à 1280 x 720.

- La résolution cible pour Visual Studio est **1366 x 768**. Il s’agit de la résolution la plus faible à laquelle nous offrons une expérience utilisateur *satisfaisante* .

- La hauteur de la boîte de dialogue initiale doit être **inférieure à 700 pixels**, de sorte qu’elle s’adapte à la résolution minimale du frame IDE à 96 ppp.

### <a name="high-density-displays"></a>Affichages à haute densité
 L’interface utilisateur de Visual Studio doit fonctionner correctement dans tous les facteurs de mise à l’échelle DPI que Windows prend en charge : 150%, 200% et 250%.

## <a name="anti-patterns"></a>Anti-modèles
 Visual Studio contient de nombreux exemples d’interfaces utilisateur qui suivent nos instructions et les meilleures pratiques. Dans un souci de cohérence, les développeurs empruntent souvent des modèles de conception d’interface utilisateur de produit similaires à ceux qu’ils créent. Bien qu’il s’agisse d’une bonne approche qui nous aide à améliorer la cohérence de l’interaction avec l’utilisateur et de la conception visuelle, nous utilisons des fonctionnalités avec quelques détails qui ne respectent pas nos recommandations en raison des contraintes de planification ou de la hiérarchisation des défauts. Dans ce cas, nous ne voulons pas que les équipes copient l’un de ces « anti-modèles », car ils proliférent de l’interface utilisateur incorrecte ou incohérente au sein de l’environnement Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Champs/paramètres obligatoires affichés par défaut dans l’état d’erreur

#### <a name="feature-team-goals"></a>Objectifs de l’équipe des fonctionnalités

- Avertissez les utilisateurs qu’ils ont ajouté un élément qui doit être configuré.

- Attirez l’attention de l’utilisateur sur les zones qui nécessitent une entrée.

#### <a name="anti-pattern-solution"></a>Solution anti-modèle
 Dès que l’utilisateur a lancé une action et avant d’avoir terminé la tâche, placez immédiatement les icônes d’arrêt critique en regard des zones qui nécessitent une configuration.

#### <a name="example-manifest-designer-declarations"></a>Exemple : déclarations du concepteur de manifeste
 L’ajout d’une déclaration à la liste le place immédiatement dans un état d’erreur, qui persiste jusqu’à ce que l’utilisateur définisse les propriétés requises.

 Dans ce cas, il existe un problème supplémentaire, car l’icône utilisée pour l’alerte contient une &times; icône «», donc l’icône de suppression courante ne peut pas être utilisée en regard de celle-ci. Par conséquent, l’interface utilisateur utilise un bouton supprimer, un contrôle plus sourd.

 ![Le placement de l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-modèle")<br />Le placement de l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle Visual Studio.

#### <a name="alternatives"></a>Autres solutions

Une meilleure solution à ce problème consiste à :

- Autorisez l’utilisateur à ajouter une déclaration sans avertissement, puis à déplacer immédiatement pour définir les propriétés de l’élément.

- Ajoutez l’icône d’avertissement (triangle or) lorsque le focus se déplace à partir de l’élément, par exemple pour ajouter une autre déclaration à la liste ou pour tenter de modifier des onglets dans le concepteur.

- Si l’utilisateur tente de modifier des onglets avant de définir des propriétés sur une déclaration, affichez une boîte de dialogue indiquant que l’application n’est pas générée (ou les implications) jusqu’à ce que les avertissements soient résolus. Si l’utilisateur ignore la boîte de dialogue et modifie les onglets quand même, une icône (critique ou avertissement, le cas échéant) est ajoutée à l’onglet déclarations.

### <a name="multiple-clicks-to-dismiss-ui"></a>Plusieurs clics pour faire disparaître l’interface utilisateur

#### <a name="feature-team-goals"></a>Objectifs de l’équipe des fonctionnalités
 N’autorisez pas l’utilisateur à ignorer l’interface utilisateur sans voir d’abord le texte d’explication.

#### <a name="anti-pattern"></a>Anti-modèle
 L’équipe qui insère les liens vidéo dans différents emplacements de l’interface utilisateur de Visual Studio a choisi le modèle commun du &times; bouton de fermeture et une explication de l’info-bulle, comme spécifié par l’expérience utilisateur, et a plutôt implémenté une liste déroulante et un lien « ne plus afficher ».

#### <a name="example-video-links-in-team-explorer"></a>Exemple : liens vidéo dans Team Explorer
Forcer l’utilisateur à lire un texte explicatif avant de fermer l’interface utilisateur est un anti-modèle dans Visual Studio. Correctement conçus, les liens vidéo doivent afficher une info-bulle avec des informations supplémentaires au pointage, et cliquer sur le « &times; » doit faire disparaître le message sans avoir besoin d’une interaction supplémentaire.

 ![Le modèle de&#45;de texte explicatif &#45; incorrect](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Modèle de lien vidéo incorrect

Au lieu d’un simple bouton de fermeture (un clic), l’utilisateur est contraint d’utiliser deux clics pour faire simplement disparaître l’interface utilisateur à chaque emplacement où s’affichent les liens vidéo.

La bonne conception pour cette situation consiste à suivre le modèle commun à Internet Explorer, Office et Visual Studio : au survol, l’utilisateur peut voir la description de l’info-bulle et un clic pour masquer l’interface utilisateur.

 ![&#45;modèle de texte explicatif &#45; correct](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-pattern-correct")<br />Modèle de lien vidéo correct

### <a name="using-command-bars-for-settings"></a>Utilisation des barres de commandes pour les paramètres

La **figure A** représente cet anti-modèle : placer un paramètre sous un bouton de commande qui s’applique à plus que la commande. Dans cette esquisse, il existe des commandes autres que démarrer le débogage, comme afficher dans le navigateur, exécuter sans débogage et pas à pas détaillé, qui respecte le paramètre sélectionné.

![Figure A : anti-modèle de barre de commandes](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-figurea")<br />Figure A : anti-modèle de barre de commandes

Il est légèrement préférable de placer les paramètres de ce type dans les barres d’outils, comme illustré à la **figure B**. Tandis que les boutons partagés prennent moins d’espace et constituent par conséquent une amélioration par rapport aux listes déroulantes, les deux conceptions utilisent encore une barre d’outils pour promouvoir un élément qui n’est pas vraiment une commande.

![Figure B : mieux, mais toujours un anti-modèle de barre de commandes](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figure B : mieux, mais toujours un anti-modèle de barre de commandes

Dans l’approche correcte illustrée dans la **figure C**, le paramètre est lié à une série de commandes. Aucun paramètre global n’est défini et nous allons simplement passer d’une commande à l’autre. Il s’agit de la seule situation dans laquelle les commandes de la barre d’outils sont acceptables.

![Figure C : utilisation correcte du modèle de barre de commandes Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figure C : utilisation correcte du modèle de barre de commandes Visual Studio

### <a name="control-anti-patterns"></a>Anti-modèles de contrôle
 Certains anti-modèles sont simplement une utilisation ou une présentation incorrecte d’un contrôle ou d’un groupe de contrôles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Soulignement utilisé comme étiquette de groupe et non lien hypertexte
 Le soulignement de texte ne doit être utilisé que pour les liens hypertexte.

 **Incorrecte**\
 ![Le texte souligné qui n’est pas un lien hypertexte est un anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Le texte souligné qui n’est pas un lien hypertexte est un anti-modèle Visual Studio.

 **État**\
 ![Le style du texte non-lien hypertexte s’affiche sans ornement dans la police de l’environnement.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Le style du texte non-lien hypertexte s’affiche sans ornement dans la police de l’environnement.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Lorsque vous cliquez sur une case à cocher, une boîte de dialogue contextuelle s’affiche
 Le fait de cliquer sur la case à cocher « Activer Bureau à distance pour tous les rôles » de l’Assistant « publier des Azure Application Windows » affiche immédiatement une boîte de dialogue contextuelle, un anti-modèle Visual Studio. En outre, le champ de case à cocher ne remplit pas une case à cocher après avoir été sélectionné, un autre anti-modèle d’interaction.

 ![L’activation d’une boîte de dialogue après avoir cliqué sur une case à cocher est un anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />L’activation d’une boîte de dialogue après avoir cliqué sur une case à cocher est un anti-modèle Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Anti-modèles de lien hypertexte
 L’exemple suivant contient deux anti-modèles :

1. Le premier plan en rouge au survol signifie que la couleur partagée correcte du service de police n’est pas utilisée.

2. « En savoir plus » n’est pas le texte approprié pour un lien vers une rubrique conceptuelle. L’objectif de l’utilisateur n’est pas d’en savoir plus. il doit comprendre les ramifications de son choix.

   ![Le service de couleur est ignoré et l’utilisation de « en savoir plus » pour les liens hypertexte est l’anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Le service de couleur est ignoré et l’utilisation de « en savoir plus » pour les liens hypertexte est l’anti-modèle Visual Studio.

**Meilleure solution :** Posez la question demandée par l’utilisateur en cliquant sur le lien. Par exemple :

- Comment fonctionnent les services Windows Azure ?

- Quand ai-je besoin d’un projet Windows Azure Mobile Services ?

#### <a name="using-click-here-for-links"></a>Utilisation de « cliquez ici » pour les liens
 Les liens hypertexte doivent être explicites. Il s’agit d’un anti-modèle permettant d’utiliser « cliquez ici » ou une variante similaire.

 **Incorrect :** « Cliquez ici pour obtenir des instructions sur la création d’un nouveau projet ».

 **Bonne :** « Comment faire créer un nouveau projet ? »
