---
title: Données de diagnostic et journaux générés par le système
description: Découvrez les journaux générés par le système de Visual Studio, les types de données collectés et la façon dont ils sont utilisés pour résoudre les problèmes et améliorer la qualité du produit.
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d357b5e21ca86d7ccf11f576a15bbd0e7a90e466
ms.sourcegitcommit: a339547aa2f4e0f64b7afbcc3e1ade0a4f9287d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106171834"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Journaux générés par le système et collectés par Visual Studio

Visual Studio collecte les journaux générés par le système pour résoudre les problèmes et améliorer la qualité du produit via le [Programme d’amélioration du produit Visual Studio](visual-studio-experience-improvement-program.md). Cet article fournit des informations sur les types de données que nous recueillons et sur la façon dont nous les utilisons. Il fournit également des conseils sur la façon dont les auteurs d’extensions peuvent éviter de divulguer par inadvertance des informations personnelles ou sensibles.

## <a name="types-of-collected-data"></a>Types de données collectées

Visual Studio collecte les journaux générés par le système pour les pannes, l’absence de réponse de l’interface utilisateur et l’utilisation intensive du processeur ou de la mémoire. Nous collectons également des informations sur les erreurs rencontrées durant l’installation ou l’utilisation du produit. Les données collectées varient en fonction de l’erreur. Elles peuvent comporter des rapports des appels de procédure, des images mémoire et des informations sur les exceptions :

- En ce qui concerne l’utilisation élevée de l’UC et l’absence de réactivité, les rapports des appels de procédure relatifs aux threads Visual Studio appropriés sont collectés.

- Dans les cas où les traces de pile de certains threads ne sont pas suffisantes pour déterminer la cause racine du problème, par exemple, des pannes, une absence de réponse ou une utilisation élevée de la mémoire, nous collectons une *image* mémoire. L’image mémoire représente l’état du processus au moment où l’erreur s’est produite.

- Pour les conditions d’erreurs inattendues, par exemple, une exception durant une tentative d’écriture dans un fichier sur le disque, nous collectons des informations sur l’exception. Les informations incluent le nom de l’exception, le rapport des appels de procédure du thread où l’exception s’est produite, le message associé à l’exception et d’autres informations spécifiques à l’exception.

   L’exemple suivant de données collectées indique un nom d’exception, un rapport des appels de procédure et un message d’exception :

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Comment nous utilisons les journaux générés par le système

Le flux de travail permettant de déterminer la cause racine d’une erreur varie en fonction du type de l’erreur et de sa gravité.

### <a name="error-classification"></a>Classification de l’erreur

En fonction des journaux, les erreurs sont classées et comptabilisées pour faire l’objet d’une hiérarchisation des recherches. Par exemple, nous pouvons découvrir que «System.IO. \_ _Error. WinIOError» à « System.IO.FileStream.Init » s’est produite 500 fois dans \<x> la version du produit et a le taux d’occurrence le plus élevé dans cette version.

### <a name="work-items-for-tracking"></a>Éléments de travail pour le suivi

Des éléments de travail pour chaque erreur, par ordre de priorité, sont créés et attribués aux ingénieurs afin de faire l’objet de recherches. En règle générale, ces éléments de travail contiennent des informations relatives à la classification, à la priorité et au diagnostic en fonction du type de l’erreur. Ces informations proviennent des journaux générés par le système et collectés pour l’erreur. Par exemple, un élément de travail relatif à un plantage peut contenir le rapport des appels de procédure où se produit ce plantage.

### <a name="error-investigation"></a>Recherches liées à une erreur

Les ingénieurs utilisent les informations disponibles dans un élément de travail pour déterminer la cause racine d’une erreur. Dans certains cas, ils ont besoin de plus d’informations que celles contenues dans l’élément de travail. Ils se réfèrent donc à la collecte du journal généré par le système d’origine. Par exemple, un ingénieur peut examiner une image mémoire pour comprendre le plantage d’un produit.

## <a name="tips-for-extension-authors"></a>Conseils pour les auteurs d’extensions

Les auteurs d’extensions doivent limiter l’exposition des informations privées en évitant d’utiliser des informations personnelles ou autres informations sensibles dans les noms de modules, types et méthodes. Si un plantage ou une condition d’erreur similaire se produit avec ce code sur la pile, les informations correspondantes sont collectées dans le cadre des journaux générés par le système.

## <a name="opt-out-of-data-collection"></a>Refuser la collecte de données

Compte tenu de la finalité des données que nous collectons et des contraintes liées à leur accès et leur rétention, nous vous recommandons d’utiliser les paramètres de confidentialité par défaut pour Visual Studio et Windows. Toutefois, vous pouvez [refuser](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) de participer au Programme d’amélioration de l’expérience utilisateur Visual Studio. Lorsque vous désabonnez, vous désabonnez de la collection de données de diagnostic **facultative** . Une collecte de données de diagnostic est **nécessaire** pour s’assurer que Visual Studio est sécurisé, à jour et qu’il fonctionne comme prévu. La collecte de données de diagnostic requise n’est pas affectée par votre choix pour refuser l’VSCEIP. Pour refuser la collecte des journaux générés par le système pour tous les programmes, consultez [Diagnostics, commentaires et confidentialité dans Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Les options peuvent varier en fonction de la version de Windows que vous utilisez.

## <a name="see-also"></a>Voir aussi

- [Programme d’amélioration de l’expérience utilisateur Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostics, commentaires et confidentialité dans Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
