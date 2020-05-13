---
title: Visual Studio Debugger Glossaire (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713343"
---
# <a name="visual-studio-debugger-glossary"></a>Glossaire du débogueur Visual Studio
Ce qui suit sont [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] des termes utilisés dans le Debugging SDK.

## <a name="terms"></a>Termes
 point d’arrêt lié Une abstraction pour un point d’arrêt défini dans le code. Il existe une relation individuelle entre un point d’arrêt lié et une instruction de point d’arrêt dans le flux de code. Lorsque le code décharge, les points d’arrêt liés peuvent être débinés.

 causalité Fournit la possibilité de suivre un fil logique d’exécution à travers plusieurs fils physiques, processus et machines, et de reconstruire la pile d’appels de ce fil logique à un moment donné dans la durée de vie de ce fil.

 contexte de code Fournit une abstraction d’une position dans le code connu du moteur de débogé. Pour la plupart des architectures de temps de course, un contexte de code est une adresse dans le flux d’instructions d’un programme. Pour les langues non traditionnelles, dans lesquelles le code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.

 voie de code Représente un point d’exécution dans le code où une branche est prise ou un appel de fonction est fait. Une trace de pile est essentiellement une liste de chemins de code d’appel de fonction.

 moteur débogé (DE) Un composant qui permet de déboguer une architecture de temps de course. Un moteur de déboguer fonctionne en conjonction avec l’interprète ou le système d’exploitation et fournit des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation de l’expression.

 contexte de document Fournit une abstraction d’une position dans un document de fichier source connu du moteur de débogé. Pour la plupart des langues, un contexte de document est une position dans un fichier source. Pour les langues non traditionnelles, pour lesquelles le fichier source peut ne pas être texte, un contexte de document peut être représenté par d’autres moyens. Voir aussi *la position du document*.

 la position du document fournit une abstraction d’une position dans un fichier source connu de l’IDE. Pour la plupart des langues, une position de document est une position dans un fichier source. Pour les langues non traditionnelles, une position de document peut être représentée d’autres façons. Voir aussi *le contexte du document*.

 point d’erreur Une abstraction pour décrire une erreur dans un point d’arrêt en attente. Un point d’arrêt d’erreur peut décrire une erreur dans l’emplacement du point d’arrêt en attente, l’expression associée au point d’arrêt en attente, ou d’autres informations qui empêchent le point d’arrêt en attente de se lier à un emplacement de code.

 contexte d’évaluation Fournit une abstraction d’un contexte de programmation pour l’évaluation de l’expression. En règle générale, un contexte d’évaluation est une portée. Lors de l’évaluation de l’expression dans un contexte d’expression, le contexte d’expression fournit des règles de portée qui correspondent à son point de création. Par exemple, un contexte d’expression créé dans un cadre de pile fournira le contexte pour évaluer les variables locales, les paramètres de la méthode, les membres du groupe (le cas échéant) et les variables globales.

 exception interceptée Une exception interceptée par un moteur de déboçon, même si aucun mécanisme de manipulation d’exception n’est en place dans le cadre de la pile actuelle.

 JustMyCode Le concept de débogage seulement le code qui appartient à un utilisateur et d’ignorer tout code intermédiaire tel que le code système, même si le code source est disponible pour ce code système.

 en attendant le point d’arrêt Fournit une abstraction pour les points d’arrêt avant, pendant et après que le code est chargé et un moyen de virtualiser les points d’arrêt. Un point d’arrêt en attente:

- Contient toutes les informations nécessaires pour lier un point d’arrêt au code dans un ou plusieurs programmes.

- Peut se lier à plusieurs emplacements de code dans un ou plusieurs programmes.

- Ne se lie jamais au code.

  Chaque fois que le code se charge, tous les points d’arrêt en attente dans un programme sont vérifiés pour voir s’ils peuvent se lier. On dit qu’un point d’arrêt en attente contient tous les points d’arrêt liés qu’il lie.

  processus Un processus physique Win32. Un processus peut contenir plusieurs programmes. Voir aussi *le programme*.

  programme Un espace de nom unique fonctionnant à l’intérieur d’une architecture particulière de temps d’exécution. Voir aussi *le processus*.

  responsable de débogage de session (SDM) gère n’importe quel nombre de moteurs de déboguer un certain nombre de programmes dans plusieurs processus sur n’importe quel nombre de machines. Au niveau de base, le SDM est un multiplexeur de moteurs de débogé. En outre, le SDM fournit une vue unifiée de la session de débogage à l’IDE.

  cadre de pile Représente l’état de calcul sur un cadre particulier et un niveau particulier d’appels de fonction imbriqués.

  thread La notion généralisée d’exécution d’instructions basée sur la pile en cours d’exécution dans au moins un programme.

  point d’arrêt d’avertissement Une abstraction pour décrire un avertissement dans un point d’arrêt en attente. Un point d’arrêt décrit une raison pour laquelle le point d’arrêt en attente n’a pas encore lié à un emplacement de code. Il se peut que le code n’ait pas encore chargé pour l’emplacement décrit par le point d’arrêt en attente, ou pour une autre raison.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
