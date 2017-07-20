---
title: "Guide pratique pour spécifier des commandes de pré-instrumentation et de post-instrumentation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: afbc73dbeda9d8201d1ed0cfccdf80025fc82306
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Guide pratique pour spécifier des commandes de pré-instrumentation et de post-instrumentation
Vous pouvez spécifier des commandes qui s’exécutent avant ou après l’instrumentation des fichiers binaires d’une session de performance. Vous pouvez spécifier toute commande pouvant être émise à partir de la ligne de commande comme événement de pré-instrumentation ou de post-instrumentation. Par exemple, vous pouvez spécifier des commandes qui automatisent la nouvelle signature d’un assembly avec une clé de nom fort dans un fichier de commandes exécuté une fois les fichiers binaires instrumentés.  
  
 Vous pouvez spécifier des commandes pour tous les fichiers binaires instrumentés dans le cadre de l’exécution du profilage ou pour des fichiers binaires individuels. Toutefois, vous ne pouvez spécifier qu’une seule commande de pré-instrumentation à exécuter avant le processus d’instrumentation et une seule commande de post-instrumentation à exécuter après. Vous ne pouvez pas spécifier des commandes à la fois pour tous les fichiers binaires et pour des fichiers binaires individuels. Quand vous spécifiez des commandes pour tous les fichiers binaires, les commandes sont exécutées avant ou après l’instrumentation de chaque fichier binaire de la session.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Le répertoire de travail dans lequel les commandes sont exécutées dépend du système d’exploitation où vous exécutez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] et de la plateforme cible de l’application profilée.  
  
 **Ordinateurs 32 bits**  
  
 Sur les ordinateurs 32 bits, le répertoire des outils de profilage par défaut est Lecteur\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools.  
  
 **Ordinateurs 64 bits**  
  
 Sur les ordinateurs 64 bits, spécifiez le chemin en fonction de la plateforme cible de l’application profilée :  
  
-   Pour les applications 32 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools  
  
-   Pour les applications 64 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Pour spécifier des commandes de pré-instrumentation  
  
1.  Effectuez l’une des opérations suivantes :  
  
    -   Pour spécifier des commandes de pré-instrumentation pour l’ensemble des fichiers binaires dans une session de performance, sélectionnez le nœud de la session de performance dans l’**Explorateur de performances**, puis cliquez avec le bouton droit et sélectionnez **Propriétés**.  
  
    -   Pour spécifier des commandes de pré-instrumentation pour un fichier binaire spécifique, cliquez avec le bouton droit sur le nom du fichier binaire dans la liste **Cibles** de la session de performance, puis sélectionnez **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages de propriétés**, cliquez sur **Instrumentation**.  
  
3.  Tapez la commande dans la zone de texte **Ligne de commande** sous **Événements de pré-instrumentation**.  
  
    > [!NOTE]
    >  Vous pouvez cliquer sur le bouton de sélection **(...)** à côté de la zone **Ligne de commande** pour rechercher et sélectionner le fichier .exe, .cmd ou .bat approprié.  
  
4.  Cliquez sur **OK**.  
  
     Pour empêcher la commande de s’exécuter sans la supprimer, cochez la case **Exclure de l’instrumentation**. Pour modifier les paramètres du compilateur ou de l’éditeur de liens, utilisez les pages de propriétés du projet.  
  
### <a name="to-specify-post-instrument-commands"></a>Pour spécifier des commandes de post-instrumentation  
  
1.  Effectuez l’une des opérations suivantes :  
  
    -   Pour spécifier des commandes de post-instrumentation pour l’ensemble des fichiers binaires dans une session de performance, sélectionnez le nœud de la session de performance dans l’**Explorateur de performances**, puis cliquez avec le bouton droit et sélectionnez **Propriétés**.  
  
    -   Pour spécifier des commandes de post-instrumentation pour un fichier binaire spécifique, cliquez avec le bouton droit sur le nom du fichier binaire dans la liste **Cibles** de la session de performance, puis sélectionnez **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages de propriétés**, cliquez sur **Instrumentation**.  
  
3.  Tapez la commande dans la zone de texte **Ligne de commande** sous **Événements de post-instrumentation**.  
  
    > [!NOTE]
    >  Vous pouvez cliquer sur le bouton de sélection **(...)** à côté de la zone **Ligne de commande** pour rechercher et sélectionner le fichier .exe, .cmd ou .bat approprié.  
  
4.  Cliquez sur **OK**.  
  
     Pour empêcher la commande de s’exécuter sans la supprimer, cochez la case **Exclure de l’instrumentation**. Pour modifier les paramètres du compilateur ou de l’éditeur de liens, utilisez les pages de propriétés du projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)
