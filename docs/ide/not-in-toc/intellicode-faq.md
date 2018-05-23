---
title: Questions fréquentes (FAQ) sur IntelliCode
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: df5ce60e9d7a05d8cc7c9ebbe173dd30a0a0edf4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2018
---
# Questions fréquentes (FAQ) sur Visual Studio IntelliCode

Merci de vous intéresser à Visual Studio IntelliCode ! Nous espérons que ce petit FAQ répondra à certaines des questions que vous vous posez peut-être.

## Q. Qu’est-ce que Visual Studio IntelliCode ?

Dans la Build 2018, nous avons annoncé Visual Studio IntelliCode, une nouvelle fonctionnalité qui améliore le développement logiciel avec l’intelligence artificielle (IA). IntelliCode aide les développeurs et les équipes à coder avec confiance, à trouver plus rapidement les problèmes et à se concentrer sur les revues du code.

Nous vous avons montré un premier aperçu de la façon dont IntelliCode améliore le processus de développement logiciel de plusieurs manières :

- Il fournit une complétion de code en fonction du contexte.
- Il aide les développeurs à respecter les modèles et les styles de leur équipe.
- Il trouve des problèmes de codage difficiles à détecter.
- Il facilite les revues de code en attirant l’attention sur les problèmes qui sont vraiment importants.

Les développeurs trouveront plus d’informations sur IntelliCode et pourront s’inscrire pour connaître les nouveautés et obtenir les prochaines préversions privées sur [https://aka.ms/intellicode](https://aka.ms/intellicode).

## Q. Que peuvent faire les clients avec Visual Studio IntelliCode ?

Visual Studio IntelliCode est constitué de différentes fonctionnalités qui offrent de nouvelles améliorations de productivité via l’intelligence artificielle (IA).

Les développeurs peuvent [télécharger une extension expérimentale](https://go.microsoft.com/fwlink/?linkid=872707) pour Visual Studio 2017 version 15.7 et ultérieure. L’extension fournit une fonctionnalité IntelliSense améliorée qui prédit l’API la plus probablement correcte que le développeur doit utiliser, au lieu de simplement présenter une liste alphabétique des membres. Elle utilise le contexte actuel du code du développeur et des modèles pour fournir cette liste dynamique. Nous allons mettre à jour l’extension en ajoutant des fonctionnalités dans les mois à venir.

## Q : En quoi « IntelliSense assisté par IA » s’appuyant sur la technologie IntelliCode est-il meilleur que la version normale d’IntelliSense ?

Avec IntelliCode, la liste de complétion suggère l’API la plus probablement correcte qu’un développeur doit utiliser, au lieu de présenter une simple liste alphabétique des membres. Il utilise le contexte actuel du code du développeur et des modèles, en se basant sur 2 000 projets open source de grande qualité ayant obtenu plus de 100 étoiles sur GitHub pour fournir cette liste dynamique. Les résultats forment un modèle qui prédit les appels d’API les plus probables et les plus pertinents.

## Q : Quelle est la qualité des suggestions de complétion de code d’IntelliCode ?

Chez Microsoft, nous utilisons les recommandations d’IntelliCode en interne depuis un certain temps et nous estimons que ces suggestions sont utiles. Mais au final, ce seront vos propres commentaires, en votre qualité de rédacteur de code, qui détermineront ses performances et son utilité réelles. Nous vous encourageons vivement à essayer l’[extension IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) de Visual Studio. N’hésitez pas à nous faire part de vos commentaires sur son usage. Nous formerons également notre modèle en fonction de ce que vous choisirez dans nos recommandations et nous mettrons à jour l’extension à mesure que le modèle s’améliorera.

> [!NOTE]
> Votre code défini par l’utilisateur ne sera pas collecté. Consultez la question sur la [confidentialité](#privacy).

## Q. Quel est l’avenir d’IntelliCode ?

Nous allons explorer de nombreuses façons d’améliorer la productivité des développeurs avec l’IA et d’autres techniques avancées. Dans la Build 2018, nous vous avons montré un premier aperçu de certains des scénarios où nous pensons que l’IA peut aider les développeurs, mais il y en a encore tant d’autres ! Nous sommes intéressés par les commentaires des développeurs qui ont testé ce que nous avons montré, alors n’hésitez pas à vous inscrire pour connaître les nouveautés et les mises à jour sur [https://aka.ms/intellicode](https://aka.ms/intellicode).

## Q. Quel est son coût ?

Nous n’avons jusqu’à présent fait aucune annonce concernant son prix.

## Q. Quand la version finale d’IntelliCode sera-t-elle disponible ?

La fonctionnalité IntelliSense assistée par IA d’IntelliCode est actuellement dans sa première préversion expérimentale. Nous allons continuer à mettre à jour l’extension expérimentale en ajoutant d’autres fonctionnalités au fil du temps. Nous n’avons aucun calendrier pour une version finale, mais nous prenons en compte les commentaires des développeurs afin de pouvoir offrir les meilleures expériences possibles. Vous pouvez vous inscrire pour connaître les nouveautés et les mises à jour sur [https://aka.ms/intellicode](https://aka.ms/intellicode).

## Q. Cette fonctionnalité est-elle disponible seulement dans Visual Studio et pour C# ?

L’expérience a été présentée dans la Build 2018 de Visual Studio 2017 sur un code base C#. Mais nous sommes impatients d’étendre IntelliCode à d’autres langages et d’autres outils de la famille Visual Studio.

## Q. De quelle version de Visual Studio ai-je besoin pour exécuter cette extension ?

L’extension IntelliCode de Visual Studio est prise en charge sur Visual Studio 2017 version 15.7 (préversion 5) et ultérieure (toutes les références SKU). L’installation de l’extension s’arrête avec le message « Cette extension n’est installée sur aucun des produits actuellement installés. » si la version minimale requise n’est pas installée sur votre ordinateur.

## Q. Cette fonctionnalité est-elle disponible seulement en anglais ?

IntelliCode est aujourd’hui une extension en préversion. Nous souhaiterions vivement connaître dans quelle mesure ces fonctionnalités son utiles pour un large éventail de clients. Quand IntelliCode ne sera plus en préversion, nous prendrons assurément vos commentaires en compte quand nous définirons les paramètres régionaux et la langue pris en charge, ainsi que le mode d’empaquetage. 

## <a name="privacy"/> Q : Qu’en est-il de la confidentialité ? Envoyez-vous mon code dans le cloud ? Quelles sont les données des clients envoyées à Microsoft ?

Les développeurs sont invités à expérimenter Visual Studio IntelliCode aujourd’hui sous la forme d’une extension en préversion expérimentale. L’objectif de l’extension est de permettre aux développeurs de tester les fonctionnalités IntelliCode et d’envoyer des commentaires à l’équipe du produit.

Nous capturons avec l’extension certaines données d’utilisation et de rapports d’erreurs anonymisées pour améliorer le produit. Aucun code défini par l’utilisateur n’est envoyé à Microsoft, mais nous collectons des informations sur votre utilisation des résultats d’IntelliCode. Les données incluent seulement les types et les membres .NET open source que vous avez sélectionnés dans la liste des suggestions d’IntelliCode. Les développeurs peuvent refuser la collecte de données de Visual Studio, ce qui désactive également la collecte de données pour l’extension IntelliCode. Dans la barre de menus, sélectionnez **Aide** > **Envoyer des commentaires** > **Paramètres**. Dans la boîte de dialogue **Programme d’amélioration du produit Visual Studio**, sélectionnez **Non, je ne souhaite pas participer**, puis sélectionnez **OK**.

L’extension IntelliCode peut demander régulièrement au développeur de répondre à une enquête, qui est également anonymisée. Les utilisateurs peuvent s’inscrire pour obtenir les nouveautés et une préversion privée, mais ce n’est actuellement pas obligatoire pour utiliser l’extension expérimentale.

Des fonctionnalités futures pourront exiger l’accès à un service, ce qui nécessitera une inscription. Nous publierons plus de détails quand ces fonctionnalités seront prêtes pour la préversion privée.
