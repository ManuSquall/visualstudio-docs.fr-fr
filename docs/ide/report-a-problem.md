---
title: Signaler un problème
description: Fournit une vue d’ensemble de l’outil Signaler un problème et inclut des définitions et états de problèmes
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 840c8af686783a365608c1fe01661569e345add1
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67309810"
---
# <a name="overview-report-a-problem"></a>Vue d’ensemble : Signaler un problème

L’outil Signaler un problème permet à la Communauté des développeurs Visual Studio de soumettre des problèmes. Chacun de vos signalements de problème devient un élément de travail dans notre système d’ingénierie, ce qui vous permet d’interagir directement avec nos équipes de produit pour nous aider à identifier et à résoudre les problèmes à fort impact. Les commentaires que vous soumettez avec des informations de diagnostics complètes sont essentiels pour améliorer la famille de produits Visual Studio. Nous vous sommes très reconnaissants de prendre le temps de signaler des problèmes.

De plus, vous pouvez voter pour les commentaires formulés par d’autres membres de la Communauté afin d’attirer davantage l’attention sur un problème et d’aider à le résoudre plus rapidement.

## <a name="problem-status"></a>État des problèmes

Une fois que vous signalez un problème, les états indiquent où en est votre envoi dans son cycle de vie. Quand les équipes Microsoft examinent vos commentaires, elles les définissent avec un état approprié.  Vous pouvez suivre la progression de vos signalements de problème au moyen des états listés ci-dessous, qui ont chacun leurs propres signification et couleur.

![État Nouveau pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/New.jpg)

L’état **Nouveau** indique que le bogue ou problème a été signalé récemment et qu’il n’a fait l’objet d’aucune action pour le moment.

- - -

![État En triage pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/Triaged.jpg)

L’état **En triage** indique que les étapes préliminaires, telles que la modération, la traduction et la vérification initiale de doublons, ont été effectuées. Votre ticket a été transmis à l’équipe technique appropriée pour qu’elle le prenne en compte.

- - -

![État Pris en compte pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/UnderConsideration.jpg)

L’état **Pris en compte** indique que Microsoft évalue l’impact de votre problème sur la Communauté, avant de lui accorder le niveau de priorité approprié. Si l’impact sur la Communauté n’est pas encore clair ou significatif, nous maintenons la supervision du problème dans cet état.

- - -

![État Examen en cours pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/UnderInvestigation.jpg)

L’état **Examen en cours** indique que les ingénieurs font leur maximum pour trouver une solution à votre problème.

- - -

![État Besoin de plus d’informations pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/NeedMoreInfo.jpg)

L’état **Besoin de plus d’informations** indique que nous avons besoin d’informations de diagnostic supplémentaires de votre part pour poursuivre l’investigation.  [Découvrez comment répondre aux demandes Besoin de plus d’informations.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed-need-more-info)

- - -

![État Résolu - En attente de mise en production pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/FixedPendingRelease.jpg)

L’état **Résolu - En attente de mise en production** indique que nous avons un correctif pour le problème et qu’il sera disponible dans une prochaine préversion ou version.  Quand le correctif est disponible dans une préversion, le problème est marqué avec une étiquette indiquant la version dans laquelle il a été résolu.

- - -

![État Fermé - Résolu pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedFixed.jpg)

L’état **Fermé - Résolu** indique que nous avons publié un correctif pour le problème. Le problème est également marqué avec une étiquette indiquant dans quelle version il a été résolu.

- - -

![État Fermé - Doublon pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedDuplicate.jpg)

L’état **Fermé - Doublon** indique que votre problème a déjà été signalé par le biais d’autres commentaires. Dans ce cas, nous vous indiquons le lien vous permettant de suivre le signalement de problème d’origine.

- - -

![État Fermé - Priorité moindre pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Fermé - Priorité moindre** Pour aider au mieux chacun des membres de notre Communauté des développeurs, nous accordons la priorité aux problèmes qui ont l’impact le plus élevé sur les clients. Bien que nous ne puissions pas résoudre ce problème particulier pour l’instant, soyez assuré que tous vos commentaires sont précieux pour améliorer Visual Studio.

- - -

![État Fermé - Pas un bogue pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedNotABug.jpg)

L’état **Fermé - Pas un bogue** indique que nous avons déterminé que la fonctionnalité signalée obéit à sa conception.

- - -

![État Fermé - Informations insuffisantes pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

L’état **Fermé - Informations insuffisantes** indique que nous n’avons pas suffisamment d’informations pour étudier la question pour vous. Nous serons heureux de reconsidérer les commentaires une fois les informations nécessaires disponibles.

- - -

![État Fermé - Autre produit pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

L’état **Fermé - Autre produit** indique que nous avons déterminé que votre problème concerne un autre produit. Consultez le commentaire de Microsoft pour connaître le produit externe concerné et les liens connexes.

- - -

![État Fermé - Ne sera pas résolu pour le signalement de problème auprès de la Communauté des développeurs](../ide/media/ProblemStates/ClosedWontFix.jpg)

L’état **Fermé - Ne sera pas résolu** indique que nous ne suivons pas le problème en raison de facteurs tels que le manque d’impact sur la Communauté ou d’alignement sur l’orientation du produit. Pour plus d’informations, consultez le commentaire de Microsoft.  Bien que nous ne puissions pas résoudre ce problème particulier, soyez assuré que tous vos commentaires sont précieux pour améliorer Visual Studio.

- - -

## <a name="faq"></a>Questions fréquentes (FAQ)

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Comment accroître les chances d’une résolution rapide de mon problème ?

Nous vous recommandons d’utiliser la recherche pour vérifier que le problème que vous êtes sur le point de soumettre n’a pas déjà été signalé. Si vous trouvez un élément existant correspondant à votre problème, suivez-le et votez pour le ticket de ce problème.

 Fournissez toutes les informations possibles pour aider nos équipes à reproduire ce à quoi vous êtes confronté.  Ces informations incluent les étapes de reproduction nécessaires, les fragments de code, les captures d’écran, les enregistrements de la reproduction, les fichiers journaux et autres artefacts.  Voici [comment signaler un problème avec Visual Studio](./how-to-report-a-problem-with-visual-studio.md).

### <a name="how-is-my-feedback-prioritized"></a>Comment mes commentaires sont-ils hiérarchisés ?

Nous recevons un grand nombre de problèmes précieux de nos clients. Pour aider au mieux chacun des membres de la Communauté des développeurs, nous traitons en priorité les commentaires qui ont l’impact le plus élevé sur la Communauté.

Si nous ne sommes pas en mesure de répondre personnellement à vos commentaires, sachez que nous leur accordons beaucoup d’importance. Soyez assuré que tous vos commentaires parviennent à l’équipe appropriée.

Nous apprécions réellement le temps que vous consacrez à l’amélioration de Visual Studio.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Quelles actions puis-je effectuer si je ne suis pas satisfait de la solution ?

Nos équipes font de leur mieux pour diagnostiquer et corriger les problèmes que vous rencontrez ; cependant, il peut arriver que vous ne soyez pas entièrement satisfait de notre recommandation. Réagissez à nos commentaires en nous indiquant exactement ce dont vous n’êtes pas satisfait ; nous ferons alors de notre mieux pour répondre à vos besoins.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Comment suis-je informé de la progression de mes commentaires ?

Les équipes techniques Microsoft communiquent avec vous en commentant le ticket de commentaires et en changeant l’état de votre ticket au fil de leur progression. Surveillez les notifications par e-mail qui sont envoyées quand l’état d’un ticket change ou qu’un commentaire est posté.  Vous pouvez gérer la fréquence des notifications dans les paramètres Profil et Préférences sur le site de la Communauté des développeurs.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Pourquoi ne puis-je pas ajouter un problème pour Visual Studio IDE sur le site web de la Communauté des développeurs ?

Le signalement d’un problème par le biais de Visual Studio permet d’inclure automatiquement les informations de diagnostic dans le rapport. Il s’agit d’informations essentielles qui fournissent à nos ingénieurs le contexte dont ils ont besoin pour comprendre votre problème et travailler à sa résolution.

Quand vous effectuez un signalement par le biais de Visual Studio, vous pouvez facilement partager des informations de diagnostic complètes avec nous, telles que de grands fichiers journaux volumineux, des informations de plantage, des captures d’écran, un enregistrement de la reproduction et autres artefacts, qui nous aident à vous fournir plus rapidement des solutions de meilleure qualité.
