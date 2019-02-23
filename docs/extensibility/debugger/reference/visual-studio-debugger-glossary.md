---
title: Glossaire du débogueur Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bca908957a98dfa9fa12b0e420a727a2798b4fc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686845"
---
# <a name="visual-studio-debugger-glossary"></a>Glossaire du débogueur Visual Studio
Les éléments suivants sont des termes utilisés dans le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de débogage.

## <a name="terms"></a>Termes
 limite de point d’arrêt une abstraction pour un point d’arrêt définie dans le code. Il existe une relation entre un point d’arrêt lié et une instruction de point d’arrêt dans le flux de code. Quand le code décharge, points d’arrêt liés peuvent annuler la liaison.

 causalité offre la possibilité de suivre un thread logique d’exécution sur plusieurs threads physiques, des processus et des machines et pour reconstruire la pile des appels de ce thread logique à un moment donné dans la durée de vie de ce thread.

 contexte de code fournit une abstraction d’une position dans le code connu du moteur de débogage. Pour la plupart des architectures d’exécution, un contexte de code est une adresse dans le flux d’instructions d’un programme. Pour les langues non traditionnel, dans lequel code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.

 chemin d’accès du code représente un point d’exécution dans le code où provient d’une branche ou un appel de fonction est effectué. Une trace de pile est essentiellement une liste de chemins de code d’appel de fonction.

 déboguer un composant moteur (dé) qui autorise le débogage d’une architecture d’exécution. Un moteur de débogage fonctionne conjointement avec le système d’exploitation ou un interpréteur et fournit des services de débogage telles que l’exécution du contrôle des points d’arrêt, évaluation et expression.

 contexte de document fournit une abstraction d’une position dans un document de fichier source connu du moteur de débogage. Pour la plupart des langages, un contexte de document est une position dans un fichier source. Pour les langues non traditionnel, pour lesquels le fichier source ne peut pas être texte, un contexte de document peut être représenté par d’autres moyens. Voir aussi *document position*.

 position du document fournit une abstraction d’une position dans un fichier source connu pour l’IDE. Pour la plupart des langages, une position de document est une position dans un fichier source. Pour les langues non traditionnel, une position de document peut être représentée par d’autres moyens. Voir aussi *contexte de document*.

 point d’arrêt d’erreur une abstraction pour la description d’une erreur dans un point d’arrêt en attente. Un point d’arrêt de l’erreur peut-être décrire une erreur dans l’emplacement du point d’arrêt en attente, l’expression associée au point d’arrêt en attente, ou d’autres informations qui empêche le point d’arrêt en attente à partir de la liaison vers un emplacement du code.

 contexte d’évaluation fournit une abstraction d’un contexte de programmation pour l’évaluation d’expression. En règle générale, un contexte d’évaluation est une étendue. Lors de la version d’évaluation de l’expression dans le contexte d’une expression, le contexte d’expression fournit des règles de portée qui correspondent à son point de la création. Par exemple, un contexte de l’expression créé dans un frame de pile fournit le contexte pour évaluer les variables locales, les paramètres de méthode, les membres de classe (le cas échéant) et les variables globales.

 intercepté exception une exception est interceptée par un moteur de débogage, même si aucun mécanisme d’exceptions ne sont en place dans le frame de pile actuel.

 JustMyCode le concept de débogage uniquement du code qui appartient à un utilisateur et en ignorant tout le code intermédiaire tel que le code du système, même si le code source est disponible pour le code de ce système.

 en attente de point d’arrêt fournit une abstraction pour les points d’arrêt avant, pendant et après le code est chargé et une méthode pour virtualiser des points d’arrêt. Un en attente de point d’arrêt :

- Contient toutes les informations nécessaires pour lier un point d’arrêt au code dans un ou plusieurs programmes.

- Peut lier à plusieurs emplacements de code dans un ou plusieurs programmes.

- Jamais de se lier au code.

  Charge de chaque code de temps, tous les points d’arrêt en attente dans un programme sont vérifiées pour voir si elles peuvent lier. Un point d’arrêt en attente est dit qu’il contient tous les points d’arrêt liés auquel elle est liée.

  traiter un processus Win32 physique. Un processus peut contenir plusieurs programmes. Voir aussi *programme*.

  Un espace de noms en cours d’exécution à l’intérieur d’une architecture d’exécution particulière du programme. Voir aussi *processus*.

  Gestionnaire de session de débogage (SDM) gère n’importe quel nombre de moteurs de débogage n’importe quel nombre de programmes dans plusieurs processus sur n’importe quel nombre d’ordinateurs de débogage. Au niveau de base, le SDM est un multiplexeur de moteurs de débogage. En outre, le SDM fournit une vue unifiée de la session de débogage à l’IDE.

  frame de pile représente l’état de calcul sur un frame particulier et niveau particulier d’appels de fonction imbriqués.

  La notion généralisée de l’exécution d’instructions basées sur la pile en cours d’exécution au moins un programme de thread.

  point d’arrêt d’avertissement une abstraction pour décrire un avertissement dans un point d’arrêt en attente. Un point d’arrêt de l’avertissement décrit une raison pour laquelle le point d’arrêt en attente n’a pas encore lié à un emplacement du code de raison. Cela peut être que le code n'a pas encore chargé pour l’emplacement indiqué par le point d’arrêt en attente, ou pour une raison quelconque.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)