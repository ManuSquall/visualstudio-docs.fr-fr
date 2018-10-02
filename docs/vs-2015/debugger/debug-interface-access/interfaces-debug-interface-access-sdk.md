---
title: Interfaces (SDK Debug Interface Access) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 430d310b4a42440d827dcefd209579b36eda9807
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516716"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfaces (Kit de développement logiciel Debug Interface Access)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Interfaces (Debug Interface Access SDK)](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/interfaces-debug-interface-access-sdk).  
  
Méthodes sont répertoriées par ordre alphabétique sous chaque interface dans la table des matières et sur la page de l’interface dans l’ordre Vtable.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Permet de contrôler comment le SDK DIA calcule les adresses virtuelles virtuels et relatifs pour les objets de débogage.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Lance l’accès à une source de symboles de débogage.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Fournit l’accès aux enregistrements dans un flux de données de débogage.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Énumère les différents flux de débogage contenues dans la source de données.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Énumère les différents éléments de données de frame contenus dans la source de données.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Énumérer les différentes sources injectés contenues dans la source de données.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Énumère les différents numéros de ligne contenues dans la source de données.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Énumère les contributions de section différents contenues dans la source de données.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Énumère les différents segments contenus dans la source de données.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Énumère les différents fichiers sources contenus dans la source de données.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Énumère les frames de pile différentes disponibles.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Énumère les différents symboles contenus dans la source de données.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Énumère les différents symboles contenus dans la source de données par adresse.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Énumère les différents tableaux contenus dans la source de données.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Expose les détails d’un frame de pile.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Expose les détails de l’emplacement et la mémoire les décalages base du module ou de l’image.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Accès le code source du programme stockées dans la source de données DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Accéder à des informations qui décrit le processus de mappage d’un bloc d’octets de texte de l’image à un numéro de ligne du fichier source.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Reçoit des rappels du symbole DIA procédure de localisation, ce qui permet une interface utilisateur pour signaler l’avancement de la tentative d’emplacement.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Reçoit des rappels de symbole DIA procédure de localisation, ce qui permet de restrictions à imposer sur le processus de localisation.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Vous permet de lire les propriétés persistantes d’un jeu de propriétés DIA.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Permet à une application cliente fournir des octets d’un fichier exécutable, tel que spécifié par la position de fichier.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Permet à une application cliente fournir des octets d’un fichier exécutable comme spécifié par une adresse virtuelle relative.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Récupère des données décrivant une contribution de la section, autrement dit, un bloc contigu de mémoire a contribué à l’image par un compiland.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Mappe les données à partir du numéro de la section à des segments de l’espace d’adressage.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Fournit un contexte de requête pour les symboles de débogage.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Représente un fichier source.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Expose les propriétés d’un frame de pile.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Fournit des méthodes permettant d’effectuer une pile de remonter à l’aide du fichier PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Gère le contexte de la pile entre les appels de la [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) (méthode).  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Facilite le parcours de la pile à l’aide du fichier de base de données (PDB) de débogage de programme.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Décrit les propriétés d’une instance de symbole.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Énumère une table de source de données DIA.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Décrit les énumérations et les structures utilisées par les diverses interfaces de DIA SDK.  
  
 [Constantes (Kit de développement logiciel Debug Interface Access)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Décrit les constantes disponibles dans le SDK DIA.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)



