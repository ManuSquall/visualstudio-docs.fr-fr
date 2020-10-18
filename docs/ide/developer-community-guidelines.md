---
title: Consignes Developer Community
description: Décrit les instructions à suivre pour travailler avec la communauté de développeurs Visual Studio.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfcdcfc309fb951b2f7e490f0d03dcfe9d381b83
ms.sourcegitcommit: 54ec951bcfa87fd80a42e3ab4539084634a5ceb4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92116148"
---
# <a name="developer-community-guidelines"></a>Consignes Developer Community

La communauté des développeurs suit des problèmes et des suggestions de fonctionnalités pour Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Envoi de problèmes et de suggestions

La [communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/) effectue le suivi des problèmes et des suggestions de fonctionnalités pour Visual Studio.

### <a name="before-submitting-an-issue"></a>Avant de soumettre un problème

Recherchez votre problème sur la communauté de développeurs Visual Studio pour vous assurer qu’il n’existe pas déjà. Si vous trouvez que votre problème existe déjà, effectuez les commentaires appropriés et effectuez un cast de votre vote.

Si votre problème est une question, demandez à la communauté [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) à l’aide de la balise _Visual Studio_. Nous proposons au personnel du support technique la surveillance de cette balise et vous aideront à répondre aux questions.

Si vous ne trouvez pas de problème existant qui décrit votre bogue ou votre fonctionnalité, soumettez un problème à l’aide des instructions ci-dessous.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Écriture d’un rapport de bogues ou d’une suggestion de fonctionnalité appropriée

- Fichier un seul problème ou demande de fonctionnalité par problème.

  - La combinaison de plusieurs problèmes ou demandes de fonctionnalités en un seul problème rend le diagnostic plus difficile pour nous, et il est plus difficile pour les autres utilisateurs de voter pour votre problème.
  - N’ajoutez pas votre problème en tant que commentaire à un problème existant, sauf s’il s’agit d’une entrée identique. De nombreux problèmes semblent similaires mais ont des causes différentes, ce qui complique le diagnostic de votre problème.

- Plus vous pouvez fournir d’informations, plus il sera facile de reproduire et résoudre votre problème.
- Incluez les étapes suivantes pour chaque problème.

  - Étapes reproductibles (1... 2... 3...) et ce que vous attendiez par rapport à ce que vous avez rencontré.
  - Des images, des animations ou un lien vers une vidéo. Les images et les animations illustrent la reproduction des étapes, mais ne les remplacent _pas_ .
  - Le cas échéant, un extrait de code qui illustre le problème ou un lien vers un référentiel de code que nous pouvons facilement extraire sur notre ordinateur pour recréer le problème.

- N’oubliez pas d’effectuer les étapes suivantes :

  - Recherche pour voir s’il existe un doublon. Si c’est le cas, voter le problème existant, en fournissant des commentaires supplémentaires ou des clarifications si nécessaire.
  - Recréez le problème après la désactivation de toutes les extensions. Si vous trouvez que le problème est causé par une extension que vous avez installée, envoyez un problème à l’extension, respectivement.
  - Simplifiez votre code autour du problème afin de pouvoir mieux isoler le problème.

Même avec des problèmes incluant des détails enrichis, nous pouvons ne pas être en mesure de reproduire le problème et de demander plus d’informations.

## <a name="managing-problem-reports"></a>Gestion des rapports de problèmes

Le triage d’un problème est un processus à plusieurs étapes qui est réalisé de façon collaborative au sein de l’équipe des fonctionnalités. Le triage prend généralement une semaine, mais peut prendre plus de temps. L’objectif du triage est de vous permettre de comprendre clairement ce qui se passe à votre problème. Par exemple, après triage, vous savez si nous prévoyons de résoudre votre problème ou d’attendre d’autres commentaires sur la communauté.

Une fois que vous signalez un problème, les états indiquent où en est votre envoi dans son cycle de vie. Au fur et à mesure que vos commentaires sont examinés par les équipes de produit Visual Studio, ils sont définis avec un état approprié. Suivez la progression de vos rapports de problèmes en référençant les [États et le Forum aux questions](./report-a-problem.md).

### <a name="prioritizing-which-issues-to-fix"></a>Définition de la priorité des problèmes à résoudre

Nous ne pouvons pas résoudre tout le problème signalé. Certaines sont trop coûteuses à corriger, certaines peuvent régresser d’autres fonctionnalités, et certaines peuvent avoir un impact trop faible. Nous comprenons que cela peut vous être utile si vous avez pris le temps de nous envoyer un rapport de problème. Nous y sommes là, que ce soit dans ce projet ou dans d’autres. Si un problème a été fermé et que vous avez le sentiment que nous n’avons pas satisfait, vous pouvez clarifier votre cas d’utilisation et demander le problème à réactiver pour une autre passe. À ce stade, nous pouvons vous demander des informations supplémentaires.

### <a name="missing-important-information"></a>Informations importantes manquantes

Lorsqu’il manque des informations importantes dans un problème, nous attribuons l’état _plus_ d’informations. Nous nous penchons sur le problème avec les informations spécifiques dont nous avons besoin et vous recevrez une notification par courrier électronique. Si nous ne recevons pas les informations dans les sept jours, nous vous enverrons un rappel. Après cela, nous fermons le ticket au bout de 14 jours d’inactivité.

### <a name="other-product"></a>Autre produit

Parfois, lorsque vous signalez un problème, il s’avère qu’il est dû à un autre produit et non à Visual Studio. Il peut s’agir d’une autre application associée ou d’une extension. 

Lorsque cela se produit, nous allons fermer le problème et vous demander de l’ouvrir avec l’autre produit. Voici quelques emplacements courants pour les fichiers de ces problèmes :

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Support Visual Studio Subscription](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Informations supplémentaires

- [Comment augmenter les chances de résolution d’un problème de performances](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Détecter un problème et créer des journaux pour les problèmes MSBuild](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Gestion des suggestions de fonctionnalités

Les suggestions de fonctionnalités sont un moyen de communication entre nous et les membres de la communauté des développeurs. Techniquement, nous pourrions conserver toutes les demandes de fonctionnalités ouvertes à l’infini. Toutefois, le maintien des problèmes ouverts réduit la visibilité de la communauté à l’état réel d’une fonctionnalité. Nous fermons donc les demandes de fonctionnalités que nous ne traiterons pas et affectons les fonctionnalités que nous pouvons adresser à l’étiquette en _cours de vérification_ .

Si vous avez suggéré une fonctionnalité, il est possible que nous ne prévoyons pas de traiter votre demande. Nous comprenons cela. Nous avons tous déjà participé à ce projet ou à d’autres personnes. Nous sommes donc assurés que nous aimons tous vos commentaires. Ne vous inquiétez pas de l’infraction personnelle quand nous fermons ou attribuons l’étiquette en _cours de révision_ à votre suggestion. Si vous estimez que votre suggestion de fonctionnalité mérite de rester ouverte, Clarifiez votre cas d’utilisation et contactez-nous ou rassemblez plus de votes.

Dans le processus de prise de décision, nous examinons les caractéristiques suivantes de la suggestion de fonctionnalité :

- Correspond-il à notre orientation générale du produit ?
- Pouvons-nous nous permettre de la générer et de la gérer ?
- S’aligne-t-il avec notre stratégie générale de feuille de [route](/visualstudio/productinfo/vs-roadmap) ?
- Bénéficie-t-il d’un support communautaire, comme indiqué par les votes et les commentaires ?
- Nous l’aimons, même avec une faible prise en charge de la communauté ?

Quand nous ne pouvons pas répondre « oui » à l’une de ces questions, nous allons la fermer. Mais souvent, la suggestion reste ouverte en cours d' _examen_ pour recueillir des commentaires sur la communauté.

Si une suggestion ne correspond pas à notre orientation globale du produit, nous allons la fermer en *dehors de l’étendue*. Par exemple, il peut y avoir des investissements similaires dans d’autres membres de la famille de produits Visual Studio. Ou la fonctionnalité suggérée ne peut être pertinente que pour quelques personnes, ce qui rend une extension mieux adaptée pour la fournir.

Suivez la progression de votre suggestion de fonctionnalité en référençant les [États de suggestion et le Forum aux questions](./report-a-problem.md).

## <a name="discussion-etiquette"></a>Étiquette de discussion

Pour que la conversation reste claire et transparente, limitez la discussion à l’anglais et gardez les choses pertinentes pour le problème. Envisagez d’autres personnes et essayez toujours d’être courtois et professionnel.

Pour plus d’informations, consultez le [Code de la communauté Microsoft](https://answers.microsoft.com/en-us/page/codeofconduct).

Toute violation de l’étiquette de discussion peut entraîner la suppression du commentaire et éventuellement interdire l’utilisateur.

## <a name="data-privacy"></a>Confidentialité des données

Les commentaires et les réponses sont visibles publiquement, mais tous les fichiers joints sont partagés en privé avec Microsoft uniquement. Cette visibilité est avantageuse, car elle permet à la communauté entière de voir les problèmes et solutions détectés par d’autres utilisateurs. Si vous êtes préoccupé par la confidentialité de vos données ou de votre identité, vous disposez d’options. En savoir plus sur la confidentialité des données de la [communauté des développeurs](./developer-community-privacy.md).

## <a name="next-steps"></a>Étapes suivantes

Connectez-vous à la [communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/) pour signaler des problèmes, suggérer des fonctionnalités ou parcourir les tickets existants. Vous n’avez plus qu’à l’utiliser !
