---
title: UX Essentials pour Visual Studio (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698333"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials pour Visual Studio

## <a name="best-practices"></a>meilleures pratiques recommandées.

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Soyez cohérent dans l’environnement Visual Studio.

- Suivez [les modèles d’interaction existants](interaction-patterns-for-visual-studio.md) à l’intérieur de la coque.

- Caractéristiques de conception pour être compatibles avec le langage visuel de la coquille et les exigences de [l’artisanat](evaluation-tools-for-visual-studio.md).

- Utilisez des commandes et des contrôles partagés lorsqu’ils existent.

- Comprendre la hiérarchie Visual Studio et comment il établit le contexte et conduit l’interface utilisateur.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Utilisez le service environnement pour les polices et les couleurs.

- L’interface utilisateur doit respecter le réglage actuel [de la police de l’environnement](fonts-and-formatting-for-visual-studio.md) à moins qu’elle ne soit exposée pour la personnalisation dans la page Fonts et Couleurs dans le dialogue Options.

- Les éléments d’interface utilisateur doivent utiliser le [service VSColor,](colors-and-styling-for-visual-studio.md)à l’aide de jetons d’environnement partagés ou de jetons spécifiques aux fonctionnalités.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Rendre toutes les images compatibles avec le nouveau style VS.

- Suivez les principes de conception visual Studio pour les icônes, les glyphes et d’autres graphiques.

- Ne placez pas le texte dans des éléments graphiques.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Concevoir d’un point de vue centré sur l’utilisateur.

- Créez le flux de tâches avant que les caractéristiques individuelles ne s’y trouvent.

- Soyez familier avec vos utilisateurs et de rendre cette connaissance explicite dans votre spécification.

- Lors de l’examen de l’interface utilisateur, évaluer l’expérience complète ainsi que les détails.

- Concevez votre interface utilisateur de façon à ce qu’elle reste fonctionnelle et attrayante, quel que soit le lieu ou la langue.

## <a name="screen-resolution"></a>Résolution de l’écran

### <a name="minimum-resolution"></a>Résolution minimale

- La résolution minimale pour Visual Studio 2015 est **1280x720**. Cela signifie qu’il est *possible* d’utiliser Visual Studio à cette résolution, bien qu’il pourrait ne pas être une expérience utilisateur optimale. Il n’y a aucune garantie que tous les aspects seront utilisables à des résolutions inférieures à 1280x720.

- La résolution cible pour Visual Studio est **1366x768**. Il s’agit de la résolution la plus basse à laquelle nous promettons une *bonne* expérience utilisateur.

- La hauteur initiale de dialogue devrait être **inférieure à 700 pixels,** de sorte qu’elle s’inscrit dans la résolution minimale du cadre IDE à 96 dpi.

### <a name="high-density-displays"></a>Affichages à haute densité
 L’interface utilisateur dans Visual Studio doit bien fonctionner dans tous les facteurs de mise à l’échelle DPI que Windows prend en charge hors de la boîte: 150%, 200%, et 250%.

## <a name="anti-patterns"></a>Anti-modèles
 Visual Studio contient de nombreux exemples d’interface utilisateur qui suivent nos lignes directrices et les meilleures pratiques. Dans un effort pour être cohérent, les développeurs empruntent souvent à des modèles de conception d’interface utilisateur de produit semblables à ce qu’ils construisent. Bien qu’il s’agisse d’une bonne approche qui nous aide à assurer la cohérence dans l’interaction avec l’utilisateur et la conception visuelle, nous faisons à l’occasion des fonctionnalités de navire avec quelques détails qui ne répondent pas à nos lignes directrices en raison de contraintes de calendrier ou de priorisation des défauts. Dans ces cas, nous ne voulons pas que les équipes copient l’un de ces « anti-modèles » parce qu’elles prolifèrent une mauvaise ou incohérente interface utilisateur dans l’environnement Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Champs/paramètres requis indiqués dans l’état d’erreur par défaut

#### <a name="feature-team-goals"></a>Objectifs de l’équipe de fonctionnalité

- Avertissez les utilisateurs qu’ils ont ajouté un élément qui doit être configuré.

- Attirer l’attention de l’utilisateur sur les zones qui ont besoin d’entrée.

#### <a name="anti-pattern-solution"></a>Solution anti-modèle
 Dès que l’utilisateur a lancé une action et avant qu’ils aient terminé la tâche, placez immédiatement des icônes critiques à côté des zones qui ont besoin de configuration.

#### <a name="example-manifest-designer-declarations"></a>Exemple : Déclarations manifestes de concepteur
 L’ajout d’une déclaration à la liste la place immédiatement dans un état d’erreur, qui persiste jusqu’à ce que l’utilisateur fixe les propriétés requises.

 Dans ce cas, il ya une préoccupation supplémentaire parce&times;que l’icône utilisée pour l’alerte contient une icône " " , de sorte que l’icône de suppression commune ne peut pas être utilisé à côté d’elle. En conséquence, l’interface utilisateur utilise un bouton Supprimer, un contrôle plus maladroit.

 ![Placer l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifesteDesignererrordeclarationsanti-pattern")<br />Placer l’interface utilisateur dans un état d’erreur par défaut est un anti-modèle Visual Studio.

#### <a name="alternatives"></a>Autres solutions

Une meilleure solution à ce problème est de :

- Permettre à l’utilisateur d’ajouter une déclaration sans avertissement, puis déplacez immédiatement pour définir les propriétés sur l’élément.

- Ajoutez l’icône d’avertissement (triangle d’or) lorsque la mise au point se déplace de l’élément, par exemple pour ajouter une autre déclaration à la liste ou pour tenter de changer les onglets au sein du concepteur.

- Si l’utilisateur tente de changer d’onglet avant de définir des propriétés sur des déclarations, faites un dialogue expliquant que l’application ne construira pas (ou quelles que soient les implications) jusqu’à ce que les avertissements soient résolus. Si l’utilisateur rejette le dialogue et change d’onglet de toute façon, alors une icône (critique ou avertissement, le cas échéant) est ajoutée à l’onglet Déclarations.

### <a name="multiple-clicks-to-dismiss-ui"></a>Plusieurs clics pour rejeter l’interface utilisateur

#### <a name="feature-team-goals"></a>Objectifs de l’équipe de fonctionnalité
 Ne permettez pas à l’utilisateur de rejeter l’interface utilisateur sans d’abord voir le texte d’explication.

#### <a name="anti-pattern"></a>Anti-modèle
 L’équipe insérant les liens vidéo dans divers endroits au sein&times;de l’interface utilisateur VS a décidé contre le modèle commun de la "bouton étroit et l’explication de bout d’outils comme spécifié par UX, et a plutôt mis en œuvre un drop-down et "Don’t show again" lien.

#### <a name="example-video-links-in-team-explorer"></a>Exemple : Liens vidéo dans Team Explorer
Forcer l’utilisateur à lire du texte explicatif avant de rejeter l’interface utilisateur est un anti-modèle au sein de Visual Studio. Correctement conçus, les liens vidéo doivent afficher un tooltip avec&times;des informations supplémentaires sur le vol stationnaire, et en cliquant sur le " devrait rejeter le message sans avoir besoin d’une interaction supplémentaire.

 ![Modèle explicatif de texte anti&#45;&#45; incorrect](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Mauvaise utilisationofmultipleclicks")<br />Modèle incorrect de lien vidéo

Au lieu d’un simple bouton étroit (un clic), l’utilisateur est obligé d’utiliser deux clics pour simplement rejeter l’interface utilisateur dans tous les lieux où les liens vidéo apparaissent.

La conception correcte pour cette situation est de suivre le modèle commun à Internet Explorer, Office, et Visual Studio: sur le plan station, l’utilisateur peut voir la description de l’outiltip et un clic cache l’interface utilisateur.

 ![Texte explicatif anti&#45;modèle &#45; correct](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explicatiftextanti-modèle-correct")<br />Correct modèle de lien vidéo

### <a name="using-command-bars-for-settings"></a>Utilisation de barres de commande pour les paramètres

**La figure A** représente cet anti-modèle : mettre un réglage sous un bouton de commande qui s’applique à plus que la commande. Dans cette esquisse, il ya des commandes en plus de Démarrer Debugging - comme View in Browser, Start Without Debugging, et Step Into - qui respectera le paramètre sélectionné.

![Figure A : Interdiction anti-modèle de barre de commande](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figure A : Interdiction anti-modèle de barre de commande

Légèrement mieux, mais toujours indésirable, met des paramètres de ce type dans les barres d’outils, comme le montre **la figure B**. Alors que les boutons fendus prennent moins d’espace et sont donc une amélioration par rapport aux abandons, les deux conceptions sont toujours en utilisant une barre d’outils pour promouvoir quelque chose qui n’est pas vraiment une commande.

![Figure B: Mieux, mais toujours une barre de commande anti-modèle](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-modèle-FigureB")<br />Figure B: Mieux, mais toujours une barre de commande anti-modèle

Dans la bonne approche indiquée dans **la figure C**, le paramètre est lié à une série de commandes. Il n’y a pas de cadre global en cours d’installation et nous ne faisons que passer d’une commande à l’autre. C’est la seule situation dans laquelle les commandes dans la barre d’outils sont acceptables.

![Figure C : Utilisation correcte du modèle de barre de commande Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figure C : Utilisation correcte du modèle de barre de commande Visual Studio

### <a name="control-anti-patterns"></a>Contrôle des anti-modèles
 Certains anti-modèles sont tout simplement l’utilisation incorrecte ou la présentation d’un contrôle ou d’un groupe de contrôles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Soulignant l’utilisation comme étiquette de groupe, pas un hyperlien
 Le texte de soulignement ne doit être utilisé que pour les hyperliens.

 **Mauvais:**\
 ![Le texte souligné qui n’est pas un hyperlien est un anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Le texte souligné qui n’est pas un hyperlien est un anti-modèle Visual Studio.

 **Bon:**\
 ![Doté correctement, le texte non hyperlien apparaît sans ornement dans la police de l’environnement.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Doté correctement, le texte non hyperlien apparaît sans ornement dans la police de l’environnement.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Cliquer sur une case à cocher se traduit par un dialogue pop-up
 En cliquant sur la case à cocher "Active Remote Desktop pour tous les rôles" dans l’assistant "Publish Windows Azure Application" apporte immédiatement un dialogue pop-up, un visual Studio anti-modèle. En outre, le champ de la case à cocher ne se remplit pas d’une case à cocher après avoir été sélectionné, un autre anti-modèle d’interaction.

 ![L’introduction d’un dialogue après avoir cliqué sur une case à cocher est un anti-modèle Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />L’introduction d’un dialogue après avoir cliqué sur une case à cocher est un anti-modèle Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Anti-modèles de lien hypertexte
 L’exemple suivant contient deux anti-modèles :

1. Le premier plan tournant rouge sur le plan stationnaire signifie que la couleur partagée correcte du service de police n’est pas utilisée.

2. "En savoir plus" n’est pas le texte approprié pour un lien vers un sujet conceptuel. Le but de l’utilisateur n’est pas d’en savoir plus, c’est de comprendre les ramifications de son choix.

   ![Ignorer le service de couleur et en utilisant "En savoir plus" pour les hyperliens sont Visual Studio anti-modèles.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorer le service de couleur et en utilisant "En savoir plus" pour les hyperliens sont Visual Studio anti-modèles.

**Meilleure solution :** Poser la question que l’utilisateur poserait en cliquant sur le lien. Par exemple :

- Comment fonctionnent les services Windows Azure ?

- Quand ai-je besoin d’un projet Windows Azure Mobile Services ?

#### <a name="using-click-here-for-links"></a>Utilisation de "Cliquez ici" pour les liens
 Les hyperliens doivent être auto-descriptifs. Il s’agit d’un anti-modèle d’utiliser "Cliquez ici" ou toute variation similaire.

 **Mauvais:** "Cliquez ici pour obtenir des instructions sur la façon de créer un nouveau projet."

 **Bon:** « Comment puis-je créer un nouveau projet ? »
