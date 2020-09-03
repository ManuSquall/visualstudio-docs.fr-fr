---
title: Glossaire du débogueur Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713343"
---
# <a name="visual-studio-debugger-glossary"></a>Glossaire du débogueur Visual Studio
Voici les termes utilisés dans le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Kit de développement logiciel (SDK) de débogage.

## <a name="terms"></a>Termes
 point d’arrêt lié une abstraction pour un point d’arrêt défini dans le code. Il existe une relation un-à-un entre un point d’arrêt lié et une instruction de point d’arrêt dans le flux de code. Lors du déchargement du code, les points d’arrêt liés peuvent être dissociés.

 la causalité offre la possibilité d’effectuer le suivi d’un thread logique d’exécution sur plusieurs threads physiques, processus et ordinateurs, et de reconstruire la pile des appels de ce thread logique à un point donné dans la durée de vie de ce thread.

 le contexte de code fournit une abstraction d’une position dans le code connue du moteur de débogage. Pour la plupart des architectures Runtime, un contexte de code est une adresse dans le flux d’instructions d’un programme. Pour les langages non traditionnels, dans lesquels le code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.

 le chemin de code représente un point d’exécution dans le code où une branche est prise ou un appel de fonction est effectué. Une trace de la pile est essentiellement une liste de chemins de code d’appel de fonction.

 moteur de débogage (DE) un composant qui autorise le débogage d’une architecture au moment de l’exécution. Un moteur de débogage fonctionne conjointement avec l’interpréteur ou le système d’exploitation et fournit des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation d’expression.

 le contexte de document fournit une abstraction d’une position dans un document de fichier source connu du moteur de débogage. Pour la plupart des langues, un contexte de document est une position dans un fichier source. Pour les langues non traditionnelles, pour lesquelles le fichier source peut ne pas être du texte, un contexte de document peut être représenté par d’autres moyens. Voir aussi *position du document*.

 la position du document fournit une abstraction d’une position dans un fichier source connu de l’IDE. Pour la plupart des langues, une position de document est une position dans un fichier source. Pour les langages non traditionnels, une position de document peut être représentée d’autres façons. Voir aussi *contexte de document*.

 point d’arrêt d’erreur une abstraction pour la description d’une erreur dans un point d’arrêt en attente. Un point d’arrêt d’erreur peut décrire une erreur à l’emplacement du point d’arrêt en attente, l’expression associée au point d’arrêt en attente, ou d’autres informations qui empêchent le point d’arrêt en attente de se lier à un emplacement de code.

 le contexte d’évaluation fournit une abstraction d’un contexte de programmation pour l’évaluation d’expression. En règle générale, un contexte d’évaluation est une étendue. Lorsque vous procédez à une évaluation d’expression dans un contexte d’expression, le contexte d’expression fournit des règles d’étendue qui correspondent à son point de création. Par exemple, un contexte d’expression créé dans un frame de pile fournit le contexte pour l’évaluation des variables locales, des paramètres de méthode, des membres de classe (le cas échéant) et des variables globales.

 Exception interceptée Exception interceptée par un moteur de débogage, même si aucun mécanisme de gestion des exceptions n’est en place dans le frame de pile actuel.

 JustMyCode le concept de débogage du code qui appartient à un utilisateur et d’ignorer tout le code intermédiaire tel que le code système, même si le code source est disponible pour ce code système.

 le point d’arrêt en attente fournit une abstraction pour les points d’arrêt avant, pendant et après le chargement du code et une façon de virtualiser les points d’arrêt. Un point d’arrêt en attente :

- Contient toutes les informations nécessaires pour lier un point d’arrêt à du code dans un ou plusieurs programmes.

- Peut être lié à plusieurs emplacements de code dans un ou plusieurs programmes.

- Ne se lie jamais à du code.

  Chaque fois que le code est chargé, tous les points d’arrêt en attente dans un programme sont vérifiés pour voir s’ils peuvent être liés. Un point d’arrêt en attente est dit contenir tous les points d’arrêt liés qu’il lie.

  traitez un processus Win32 physique. Un processus peut contenir plusieurs programmes. Voir aussi *programme*.

  programmer un espace de noms unique s’exécutant dans une architecture d’exécution particulière. Voir aussi *processus*.

  le gestionnaire de débogage de session (SDM) gère un nombre quelconque de moteurs de débogage déboguant un nombre quelconque de programmes dans plusieurs processus sur un nombre quelconque d’ordinateurs. Au niveau de base, le SDM est un multiplexeur de moteurs de débogage. En outre, le SDM fournit une vue unifiée de la session de débogage à l’IDE.

  frame de pile représente l’état du calcul sur un frame particulier et un niveau particulier d’appels de fonction imbriqués.

  thread : notion généralisée de l’exécution d’instructions basées sur la pile qui s’exécute dans au moins un programme.

  point d’arrêt d’avertissement une abstraction pour la description d’un avertissement dans un point d’arrêt en attente. Un point d’arrêt d’avertissement décrit une raison pour laquelle le point d’arrêt en attente n’est pas encore lié à un emplacement de code. Cela peut être dû au fait que le code n’a pas encore été chargé pour l’emplacement décrit par le point d’arrêt en attente, ou pour une raison quelconque.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
