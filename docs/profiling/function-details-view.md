---
title: "Vue Informations relatives à la fonction | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c45571132fb06a63a8193d21941bbd50ccad4f42
ms.lasthandoff: 02/22/2017

---
# <a name="function-details-view"></a>Vue Informations relatives à la fonction
La fenêtre **Vue Informations relatives à la fonction** affiche les informations suivantes :  
  
-   Le graphique à barres **Distribution des coûts** représente les relations entre une fonction que vous sélectionnez et les fonctions d’appel qui ont exécuté la fonction sélectionnée, et entre la fonction sélectionnée et les fonctions appelées par cette fonction.  
  
-   Le tableau **Détails des performances de la fonction**, qui affiche des données de profilage résumées pour la fonction que vous spécifiez.  
  
-   La fenêtre **Affichage du code de fonction**, qui affiche le code de fonction quand le code est disponible.  
  
 La fenêtre **Affichage du code de fonction** est un volet distinct. Par défaut, les deux volets sont fractionnés horizontalement, et la fenêtre **Affichage du code de fonction** est positionnée en bas du cadre.  
  
-   Pour fractionner les deux volets verticalement, cliquez sur **Diviser l’écran verticalement** dans la barre d’outils.  
  
-   Pour modifier la taille relative des volets, cliquez sur la bordure ombrée entre les cadres et faites-la glisser vers un autre emplacement.  
  
## <a name="cost-distribution-bar-chart"></a>Graphique à barres Distribution des coûts  
  
### <a name="performance-metrics"></a>Métriques de performances  
 Dans la liste déroulante **Métrique de performances**, vous pouvez spécifier les valeurs qui apparaissent dans la vue. Les valeurs disponibles dépendent de la méthode de profilage qui a été utilisée dans le fichier de données de profilage. Les noms entre parenthèses sont les noms des lignes dans le tableau **Détails des performances de la fonction**.  
  
### <a name="bar-chart"></a>Graphique à barres  
 **Fonctions appelantes**  
  
 La barre **Fonctions appelantes** affiche les fonctions qui ont appelé la fonction sélectionnée. La taille du bloc qui contient la fonction appelante est proportionnelle à la contribution de la fonction appelante à la valeur totale de la métrique de performances pour la fonction sélectionnée.  
  
 Vous pouvez cliquer sur le nom d’une fonction appelante pour la sélectionner dans la vue.  
  
-   S’il y a trop de fonctions appelantes à répertorier, les fonctions avec les plus petites contributions sont regroupées dans un bloc **Autres**. Cliquez sur **Autres** pour afficher toutes les fonctions appelantes et appelées de la fonction sélectionnée dans la fenêtre **Vue Appelant/Appelé**. Pour plus d’informations, consultez [Vue Appelant/Appelé](../profiling/caller-callee-view.md).  
  
-   S’il n’y a aucune fonction appelante ou si la fonction est la fonction d’entrée d’un thread ou d’un processus, un bloc **Haut de la pile** apparaît.  
  
 **Fonction sélectionnée**  
  
 La barre de fonction sélectionnée affiche les contributions des fonctions appelées et du code dans la fonction sélectionnée pour la métrique de performances totale de la fonction sélectionnée. La taille du bloc qui contient une fonction appelée ou le corps de fonction est proportionnelle à sa contribution à la valeur totale de la métrique de performances pour la fonction sélectionnée.  
  
 Vous pouvez cliquer sur le nom d’une fonction appelée pour la sélectionner dans la vue.  
  
-   La valeur **Total** est la métrique de performances pour la fonction sélectionnée.  
  
-   Le bloc **Corps de la fonction** représente la part de la valeur totale de la métrique de performances qui s’est produite dans l’exécution directe de code dans le corps de la fonction.  
  
-   Les fonctions appelées par la fonction sélectionnée sont répertoriées dans des blocs. La taille du bloc de fonctions sélectionné représente la part de la métrique de performances totale pour la fonction sélectionnée qui s’est produite dans la fonction appelée.  
  
-   S’il y a trop de fonctions appelantes à répertorier, les fonctions avec les plus petites contributions sont regroupées dans un bloc **Autres**. Cliquez sur **Autres** pour afficher toutes les fonctions appelantes et appelées de la fonction sélectionnée dans la fenêtre **Vue Appelant/Appelé**. Pour plus d’informations, consultez [Vue Appelant/Appelé](../profiling/caller-callee-view.md).  
  
-   S’il n’y a aucune fonction appelée, un bloc **Bas de la pile** apparaît.  
  
## <a name="function-performance-details"></a>Détails des performances de la fonction  
 Le tableau Détails des performances de la fonction fournit des données de résumé pour les métriques de performances de la fonction sélectionnée. La valeur et le pourcentage sont tous deux affichés. Vous spécifiez les données de profilage qui apparaissent dans le graphique et le tableau de détails dans la liste **Métrique de performances**.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Exclusif**|-   Part de la métrique de performances qui s’est produite dans l’exécution du corps de la fonction.|  
|**Dans les appels**|-   Part de la métrique de performances qui s’est produite dans des fonctions appelées par la fonction sélectionnée.|  
|**Inclusive Total**|-   Total des valeurs **Exclusif** et **Dans les appels**.|  
  
## <a name="function-code-view"></a>Affichage du code de fonction  
 La fenêtre **Affichage du code de fonction** affiche une liste du code source quand il est disponible. En regard des lignes de code source qui appellent d’autres fonctions, une colonne grisée contient les valeurs de métriques de performances pour la fonction appelée. Pour modifier le code source, cliquez sur le lien vers le fichier de code source.  
  
## <a name="cost-distribution-bar-chart-values"></a>Valeurs du graphique à barres Distribution des coûts  
  
### <a name="sampling"></a>Échantillonnage  
 Le tableau suivant explique les valeurs de la liste Métrique de performances pour les données de profilage recueillies à l’aide de la méthode d’échantillonnage.  
  
|||  
|-|-|  
|**Échantillons inclusifs (Échantillons collectés)**|-   Pour une fonction appelante, nombre d’échantillons recueillis quand la fonction sélectionnée a été appelée par cette fonction appelante.<br />-   Pour le corps de fonction, nombre d’échantillons recueillis quand la fonction sélectionnée exécutait son propre code.<br />-   Pour une fonction appelée, nombre d’échantillons recueillis quand la fonction appelée s’exécutait en raison d’un appel de la fonction sélectionnée.|  
  
### <a name="instrumentation"></a>Instrumentation  
 Le tableau suivant explique les valeurs de la liste Métrique de performances pour les données de profilage recueillies à l’aide de la méthode d’instrumentation.  
  
|||  
|-|-|  
|**Temps inclusif écoulé (Temps écoulé)**|Le temps écoulé inclut le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br /><br /> -   Pour une **Fonction appelante**, temps consacré à exécuter les instances de la fonction sélectionnée qui ont été appelées par la fonction. Cela comprend le temps passé dans des fonctions appelées par la fonction sélectionnée.<br />-   Pour le **Corps de la fonction**, temps total consacré à exécuter le code de la fonction sélectionnée. Cela exclut le temps passé dans des fonctions appelées.<br />-   Pour une fonction appelée, temps consacré à exécuter les instances de la fonction qui ont été appelées par la fonction sélectionnée. Le total comprend le temps passé dans des fonctions appelées par la fonction. Cela comprend le temps passé dans des fonctions appelées par la fonction sélectionnée.|  
|**Temps inclusif d’application (Temps d’application)**|Le temps d’application n’inclut pas le temps consacré aux appels au système d’exploitation, comme dans le cas de changements de contexte ou d’opérations d’E/S.<br /><br /> -   Pour une **Fonction appelante**, temps d’application consacré à exécuter les instances de la fonction sélectionnée qui ont été appelées par la fonction. Cela comprend le temps passé dans des fonctions appelées par la fonction sélectionnée.<br />-   Pour le **Corps de la fonction**, temps d’application total consacré à exécuter le code de la fonction sélectionnée. Cela exclut le temps passé dans des fonctions appelées.<br />-   Pour une fonction appelée, temps d’application consacré à exécuter les instances de la fonction qui ont été appelées par la fonction sélectionnée. Le total comprend le temps passé dans des fonctions appelées par la fonction.|  
  
### <a name="net-memory"></a>Mémoire .NET  
 Le tableau suivant explique les valeurs de la liste Métrique de performances pour les données de profilage recueillies à l’aide de la méthode de profilage de mémoire .NET.  
  
|||  
|-|-|  
|**Allocations inclusives (Allocations)**|-   Pour une **Fonction appelante**, nombre d’objets alloués par les instances de la fonction sélectionnée qui ont été appelées par la fonction. Ce nombre inclut les objets alloués par les fonctions appelées par la fonction sélectionnée.<br />-   Pour le **Corps de la fonction**, nombre d’objets alloués par la fonction sélectionnée quand elle exécutait son propre code. Cela exclut les objets alloués dans les fonctions appelées par la fonction sélectionnée.<br />-   Pour une fonction appelée, nombre d’objets alloués par les instances de la fonction qui ont été appelées par la fonction sélectionnée. Ce nombre inclut les objets alloués par les fonctions appelées par la fonction.|  
|**Octets inclusifs (Octets)**|-   Pour une **Fonction appelante**, nombre d’octets alloués par les instances de la fonction sélectionnée qui ont été appelées par la fonction. Ce nombre inclut les octets alloués par les fonctions appelées par la fonction sélectionnée.<br />-   Pour le **Corps de la fonction**, nombre total d’octets alloués par la fonction sélectionnée quand elle exécutait son propre code. Cela exclut les octets alloués dans les fonctions appelées par la fonction sélectionnée.<br />-   Pour une fonction appelée, nombre d’octets alloués par les instances de la fonction qui ont été appelées par la fonction sélectionnée. Ce nombre inclut les octets alloués par les fonctions appelées par la fonction.|  
  
### <a name="concurrency"></a>Concurrency  
 Le tableau suivant explique les valeurs de la liste Métrique de performances pour les données de profilage recueillies à l’aide de la méthode de concurrence.  
  
|||  
|-|-|  
|**Conflits inclusifs (Conflits)**|-   Pour une **Fonction appelante**, nombre d’événements de conflits de ressources qui se sont produits dans les instances de la fonction sélectionnée appelées par la fonction. Ce nombre inclut les événements de conflits dans les fonctions appelées par la fonction sélectionnée.<br />-   Pour le **Corps de la fonction**, nombre total d’événements de conflits qui se sont produits quand la fonction exécutait son propre code. Cela exclut les conflits se produisant dans les fonctions appelées par la fonction sélectionnée.<br />-   Pour une fonction appelée, nombre d’événements de conflits qui se sont produits dans les instances de la fonction appelées par la fonction sélectionnée. Ce nombre inclut les événements de conflits qui se sont produits dans les fonctions appelées par la fonction.|  
|**Temps bloqué inclusif (Temps bloqué)**|-   Pour une fonction appelante, temps consacré aux événements de conflits de ressources pour les instances de la fonction sélectionnée appelées par la fonction. Ce temps inclut le temps bloqué dans les fonctions appelées par la fonction sélectionnée.<br />-   Pour le **Corps de la fonction**, temps total consacré aux événements de conflits qui se sont produits quand la fonction exécutait son propre code. Cela exclut les conflits se produisant dans les fonctions appelées par la fonction sélectionnée.<br />-   Pour une fonction appelée, temps consacré aux événements de conflits de ressources pour les instances de la fonction appelées par la fonction sélectionnée. Ce temps inclut le temps bloqué dans les fonctions appelées par la fonction.|
