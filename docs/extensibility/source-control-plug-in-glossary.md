---
title: Glossaire plug-in de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699912"
---
# <a name="source-control-plug-in-glossary"></a>Glossaire de plug-in de contrôle de code source
Les termes et définitions utiles suivants se rapportent à la documentation SDK de contrôle source.

## <a name="definitions"></a>Définitions
 Checkin Lorsqu’un utilisateur apporte des modifications à une copie de travail, un utilisateur doit envoyer des modifications de la copie de travail dans le référentiel de contrôle source central. Cela crée une nouvelle révision du fichier qui est disponible pour les autres utilisateurs. Ce processus est appelé un checkin.

 Caisse L’acte de demander une copie de travail du référentiel, informer le référentiel de votre intention de le modifier. Une copie de travail reflète l’état du projet dès qu’il est vérifié.

 Programme client A qui utilise le système de contrôle du code source. Aux fins de cette documentation, c’est le Visual Studio IDE.

 Commentaire Un message décrivant les modifications qu’un utilisateur peut attacher à une révision lorsqu’une opération de contrôle source est effectuée.

 Conflit Une situation lorsque deux utilisateurs tentent d’enregistrer les modifications apportées à la même région du même fichier. En règle générale, une fusion doit être effectuée.

 Annuaire Un dossier local côté client est appelé répertoire. Il s’agit de la copie dans laquelle un utilisateur apporte effectivement des modifications. Il peut y avoir de nombreuses copies de travail d’un projet donné; généralement chaque développeur a sa propre copie.

 L’opération Get A met à jour la copie de travail de l’utilisateur avec la copie du référentiel. Contrairement à une caisse, un get est effectué lorsque l’utilisateur a simplement besoin de la dernière copie, mais a l’intention d’effectuer aucun changement.

 Historique Il s’agit généralement d’un résumé de toutes les caisses, checkins, mises à jour, balises et communiqués effectués dans le référentiel de contrôle source.

 IDE se réfère généralement à l’environnement de développement intégré Visual Studio. Toutefois, il pourrait également se référer à d’autres environnements clients qui reconnaissent l’API de contrôle source plug-in.

 Fusionner Le processus au cours duquel deux fichiers de code source ou plus sont combinés pour former un nouveau fichier qui intègre toutes les fonctionnalités des fichiers précédents. Ce concept est vital dans le contrôle de version où deux développeurs ou plus travaillent sur des fichiers en même temps.

 Projet Un dossier de contrôle source est souvent appelé un projet. Cela n’a aucune relation avec des projets ou des solutions dans Visual Studio.

 Plug-in A DLL qui fournit des fonctionnalités de contrôle des sources en implémentant l’API plug-in de contrôle source.

 Dépôt La copie principale où un système de contrôle source stocke l’historique complet de révision d’un projet. Chaque projet a exactement un référentiel.

 Révision Un changement engagé dans l’historique d’un fichier ou d’un ensemble de fichiers. Une révision est un instantané d’un projet en constante évolution.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
