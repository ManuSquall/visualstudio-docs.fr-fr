---
title: Impossible de définir le point d’arrêt de données | Microsoft Docs
description: Recherchez des explications, des solutions et des solutions de contournement pour « impossible de définir les erreurs de point d’arrêt sur variable » qui se produisent lors de l’utilisation de « arrêter lorsque la valeur change ».
ms.custom: SEO-VS-2020
ms.date: 5/19/2020
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 73e7e02d90e2a89c81b5e690718c95fe7efe0fb3
ms.sourcegitcommit: 6e27b1238a8aa704b127eac34f4173e9d56690c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110231963"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Dépannage des erreurs de point d’arrêt de données
Cette page vous guidera lors de la résolution des erreurs courantes rencontrées lors de l’utilisation de l’instruction « arrêter quand la valeur est modifiée »

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnostic des erreurs « impossible de définir le point d’arrêt des données »
> [!IMPORTANT]
> Les points d’arrêt sur les données managées sont pris en charge dans .NET Core 3,0 et les 5.0.3 et .NET. Vous pouvez télécharger la dernière version [ici](https://dotnet.microsoft.com/download).

Vous trouverez ci-dessous une liste des erreurs qui peuvent se produire lors de l’utilisation de points d’arrêt de données managés. Ils contiennent davantage d’explications sur la raison de l’erreur et des solutions possibles ou des solutions de contournement pour résoudre l’erreur.

- *«La version de .NET utilisée par le processus cible ne prend pas en charge les points d’arrêt de données. Les points d’arrêt sur variable requièrent .NET Core 3. x ou .NET 5.0.3 +, s’exécutant sur x86 ou x64.»*

  - La prise en charge des points d’arrêt sur les données managées a commencé dans .NET Core 3,0. Elle n’est actuellement pas prise en charge dans .NET Framework, les versions de .NET Core sous 3,0 ou les versions de .NET sous 5.0.3. 
    
  - **Solution**: la solution consisterait à mettre à niveau votre projet vers .net Core 3,0.

- *« La valeur est introuvable sur le tas managé et ne peut pas être suivie ».*
  - Variable déclarée sur la pile.
    - Nous ne prenons pas en charge la définition de points d’arrêt sur variable pour les variables créées sur la pile, car cette variable ne sera pas valide une fois la fonction terminée.
    - **Solution de contournement**: définissez des points d’arrêt sur les lignes où la variable est utilisée.

  - « Arrêter lorsque la valeur change » sur une variable qui n’est pas développée à partir d’une liste déroulante.
    - Le débogueur doit en interne connaître l’objet contenant le champ dont vous souhaitez effectuer le suivi. Le garbage collector peut déplacer votre objet dans le tas afin que le débogueur doive connaître l’objet qui contient la variable que vous souhaitez suivre. 
    - **Solution de contournement**: Si vous êtes dans une méthode au sein de l’objet sur lequel vous souhaitez définir un point d’arrêt sur variable, remontez d’un frame et utilisez la `locals/autos/watch` fenêtre pour développer l’objet et définir un point d’arrêt sur le champ souhaité.

- *« Les points d’arrêt sur variable ne sont pas pris en charge pour les champs statiques ou les propriétés statiques. »*
    
  - Les champs et les propriétés statiques ne sont pas pris en charge pour le moment. Si cette fonctionnalité vous intéresse, veuillez fournir [vos commentaires](#provide-feedback).

- *« Les champs et les propriétés des structs ne peuvent pas être suivis ».*

  - Les champs et les propriétés des structs ne sont pas pris en charge pour le moment. Si cette fonctionnalité vous intéresse, veuillez fournir [vos commentaires](#provide-feedback).

- *« La valeur de la propriété a changé et ne peut plus être suivie ».*

  - Une propriété peut modifier la manière dont elle est calculée au moment de l’exécution. dans ce cas, le nombre de variables dont dépend la propriété augmente et peut dépasser la limite matérielle. Consultez `"The property is dependent on more memory than can be tracked by the hardware."` ci-dessous.

- *« La propriété dépend d’un nombre de mémoire supérieur à celui qui peut être suivi par le matériel. »*
    
  - Chaque architecture possède un nombre défini d’octets et de points d’arrêt de données matérielles qu’elle peut prendre en charge, et la propriété pour laquelle vous souhaitez définir un point d’arrêt de données a dépassé cette limite. Reportez-vous au tableau des [limitations matérielles de point d’arrêt de données](#data-breakpoint-hardware-limitations) pour déterminer le nombre de composants matériels pris en charge et les octets de données disponibles pour l’architecture que vous utilisez. 
  - **Solution de contournement**: définissez un point d’arrêt sur une valeur susceptible d’être modifiée dans la propriété.

- *« Les points d’arrêt sur variable ne sont pas pris en charge lors de l’utilisation de l’évaluateur d’expression C# hérité ».*

  - Les points d’arrêt sur variable ne sont pris en charge que sur l’évaluateur d’expression C# non hérité. 
  - **Solution**: vous désactivez l’évaluateur d’expression C# hérité en accédant `Debug -> Options` alors à `Debugging -> General` décocher `"Use the legacy C# and VB expression evaluators"` .

- *« La classe **X** a une vue personnalisée du débogueur qui bloque l’utilisation des points d’arrêt de données uniquement sur les données qui lui sont spécifiques. »*
  
  - Les points d’arrêt sur variable sont uniquement pris en charge sur la mémoire qui est créée par le processus cible (l’application en cours de débogage). La mémoire sur laquelle le point d’arrêt de données est défini a été marquée comme étant éventuellement la propriété d’un objet créé par un [attribut DebuggerTypeProxy](using-debuggertypeproxy-attribute.md) ou autre chose qui ne fait pas partie du processus cible.
  - **Solution de contournement**: développez la « vue brute » du ou des objets au lieu de développer la vue DebuggerTypeProxy du ou des objets, puis définissez le point d’arrêt des données. Cela garantit que le point d’arrêt des données ne fait pas l’objet d’une mémoire appartenant à un objet créé par un attribut DebuggerTypeProxy.

## <a name="data-breakpoint-hardware-limitations"></a>Limitations matérielles des points d’arrêt de données

L’architecture (configuration de plateforme) sur laquelle votre programme s’exécute possède un nombre limité de points d’arrêt de données matériels qu’elle peut utiliser. Le tableau ci-dessous indique le nombre de registres disponibles pour une utilisation par architecture.

| Architecture | Nombre de points d’arrêt de données pris en charge par le matériel | Taille maximale en octets|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Fournir des commentaires

Pour tout problème ou suggestion concernant cette fonctionnalité, faites-le nous savoir via l’aide > envoyer des commentaires > [signaler un problème](../ide/how-to-report-a-problem-with-visual-studio.md) dans l’IDE ou dans la [communauté des développeurs](https://aka.ms/feedback/suggest?space=8).

## <a name="see-also"></a>Voir aussi

- [Utilisation de « arrêter quand la valeur change » dans .net Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog : arrêter lorsque la valeur change : points d’arrêt sur variable pour .NET Core dans Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
