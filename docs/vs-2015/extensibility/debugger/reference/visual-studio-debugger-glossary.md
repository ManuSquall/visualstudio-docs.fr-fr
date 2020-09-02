---
title: Glossaire du débogueur Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204783"
---
# <a name="visual-studio-debugger-glossary"></a>Glossaire du débogueur Visual Studio
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Voici les termes utilisés dans le [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Kit de développement logiciel (SDK) de débogage.  
  
## <a name="terms"></a>Termes  
 point d’arrêt lié  
 Abstraction d’un point d’arrêt défini dans le code. Il existe une relation un-à-un entre un point d’arrêt lié et une instruction de point d’arrêt dans le flux de code. Lors du déchargement du code, les points d’arrêt liés peuvent être dissociés.  
  
 causalité  
 Permet d’effectuer le suivi d’un thread logique d’exécution sur plusieurs threads physiques, processus et ordinateurs, et de reconstruire la pile des appels de ce thread logique à un point donné dans la durée de vie de ce thread.  
  
 Contexte de code  
 Fournit une abstraction d’une position dans le code connue du moteur de débogage. Pour la plupart des architectures Runtime, un contexte de code est une adresse dans le flux d’instructions d’un programme. Pour les langages non traditionnels, dans lesquels le code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.  
  
 chemin du code  
 Représente un point d’exécution dans le code où une branche est prise ou un appel de fonction est effectué. Une trace de la pile est essentiellement une liste de chemins de code d’appel de fonction.  
  
 moteur DE débogage (DE)  
 Composant qui autorise le débogage d’une architecture au moment de l’exécution. Un moteur de débogage fonctionne conjointement avec l’interpréteur ou le système d’exploitation et fournit des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation d’expression.  
  
 Contexte de document  
 Fournit une abstraction d’une position dans un document de fichier source connu du moteur de débogage. Pour la plupart des langues, un contexte de document est une position dans un fichier source. Pour les langues non traditionnelles, pour lesquelles le fichier source peut ne pas être du texte, un contexte de document peut être représenté par d’autres moyens. Voir aussi *position du document*.  
  
 position du document  
 Fournit une abstraction d’une position dans un fichier source connu de l’IDE. Pour la plupart des langues, une position de document est une position dans un fichier source. Pour les langages non traditionnels, une position de document peut être représentée d’autres façons. Voir aussi *contexte de document*.  
  
 point d’arrêt d’erreur  
 Abstraction pour la description d’une erreur dans un point d’arrêt en attente. Un point d’arrêt d’erreur peut décrire une erreur à l’emplacement du point d’arrêt en attente, l’expression associée au point d’arrêt en attente, ou d’autres informations qui empêchent le point d’arrêt en attente de se lier à un emplacement de code.  
  
 contexte d’évaluation  
 Fournit une abstraction d’un contexte de programmation pour l’évaluation d’expression. En règle générale, un contexte d’évaluation est une étendue. Lorsque vous procédez à une évaluation d’expression dans un contexte d’expression, le contexte d’expression fournit des règles d’étendue qui correspondent à son point de création. Par exemple, un contexte d’expression créé dans un frame de pile fournit le contexte pour l’évaluation des variables locales, des paramètres de méthode, des membres de classe (le cas échéant) et des variables globales.  
  
 Exception interceptée  
 Exception interceptée par un moteur de débogage, même si aucun mécanisme de gestion des exceptions n’est en place dans le frame de pile actuel.  
  
 JustMyCode  
 Le concept de débogage du code qui appartient à un utilisateur et d’ignorer tout le code intermédiaire tel que le code système, même si le code source est disponible pour ce code système.  
  
 point d’arrêt en attente  
 Fournit une abstraction pour les points d’arrêt avant, pendant et après le chargement du code et une méthode pour virtualiser les points d’arrêt. Un point d’arrêt en attente :  
  
- Contient toutes les informations nécessaires pour lier un point d’arrêt à du code dans un ou plusieurs programmes.  
  
- Peut être lié à plusieurs emplacements de code dans un ou plusieurs programmes.  
  
- Ne se lie jamais à du code.  
  
  Chaque fois que le code est chargé, tous les points d’arrêt en attente dans un programme sont vérifiés pour voir s’ils peuvent être liés. Un point d’arrêt en attente est dit contenir tous les points d’arrêt liés qu’il lie.  
  
  processus  
  Processus Win32 physique. Un processus peut contenir plusieurs programmes. Voir aussi *programme*.  
  
  programme  
  Un espace de noms unique s’exécutant dans une architecture d’exécution particulière. Voir aussi *processus*.  
  
  Gestionnaire de débogage de session (SDM)  
  Gère un nombre quelconque de moteurs de débogage déboguant un nombre quelconque de programmes dans plusieurs processus sur un nombre quelconque d’ordinateurs. Au niveau de base, le SDM est un multiplexeur de moteurs de débogage. En outre, le SDM fournit une vue unifiée de la session de débogage à l’IDE.  
  
  frame de pile  
  Représente l’état du calcul sur un frame particulier et un niveau particulier d’appels de fonction imbriqués.  
  
  thread  
  Notion généralisée d’exécution d’instruction basée sur la pile exécutée dans au moins un programme.  
  
  point d’arrêt d’avertissement  
  Abstraction pour la description d’un avertissement dans un point d’arrêt en attente. Un point d’arrêt d’avertissement décrit une raison pour laquelle le point d’arrêt en attente n’est pas encore lié à un emplacement de code. Cela peut être dû au fait que le code n’a pas encore été chargé pour l’emplacement décrit par le point d’arrêt en attente, ou pour une raison quelconque.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
