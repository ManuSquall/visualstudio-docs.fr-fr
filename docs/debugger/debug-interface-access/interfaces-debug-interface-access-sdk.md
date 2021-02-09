---
title: Interfaces (kit de développement logiciel de debug interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 234bfa31c79fa2c9ef60afd29d655cfc6e585aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853260"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfaces (Kit de développement logiciel Debug Interface Access)
Les méthodes sont répertoriées par ordre alphabétique sous chaque interface dans la table des matières et sur la page interface dans l’ordre vtable.

## <a name="in-this-section"></a>Dans cette section

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

Permet de contrôler la façon dont le kit de développement logiciel (SDK) DIA calcule les adresses virtuelles et virtuelles pour les objets de débogage.

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

Initie l’accès à une source de symboles de débogage.

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

Fournit l’accès aux enregistrements dans un flux de données de débogage.

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

Énumère les différents flux de débogage contenus dans la source de données.

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

Énumère les différents éléments de données de frame contenus dans la source de données.

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

Énumérez les diverses sources injectées contenues dans la source de données.

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

Énumère les différents numéros de ligne contenus dans la source de données.

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

Énumère les différentes contributions de section contenues dans la source de données.

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

Énumère les différents segments contenus dans la source de données.

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

Énumère les différents fichiers sources contenus dans la source de données.

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

Énumère les différents frames de pile disponibles.

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

Énumère les différents symboles contenus dans la source de données.

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

Énumère par adresse les différents symboles contenus dans la source de données.

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

Énumère les différentes tables contenues dans la source de données.

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

Expose les détails d’un frame de pile.

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

Expose les détails de l’emplacement de base et des décalages de mémoire du module ou de l’image.

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

Accède au code source du programme stocké dans la source de données DIA.

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

Accède aux informations qui décrivent le processus de mappage d’un bloc d’octets de texte image à un numéro de ligne de fichier source.

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

Reçoit des rappels de la procédure de localisation de symboles DIA, permettant ainsi à une interface utilisateur de signaler la progression de la tentative d’emplacement.

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

Reçoit des rappels de la procédure de localisation de symboles DIA, ce qui permet d’imposer des restrictions au processus de localisation.

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

Vous permet de lire les propriétés persistantes d’un jeu de propriétés DIA.

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

Permet à une application cliente de fournir des octets d’un fichier exécutable comme spécifié par la position de fichier.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

Permet à une application cliente de fournir des octets d’un fichier exécutable comme spécifié par une adresse virtuelle relative.

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

Récupère des données décrivant une contribution de section, autrement dit, un bloc de mémoire contigu apporté à l’image par un module de la mémoire.

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

Mappe les données du numéro de section aux segments de l’espace d’adressage.

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

Fournit un contexte de requête pour les symboles de débogage.

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

Représente un fichier source.

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

Expose les propriétés d’un frame de pile.

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

Fournit des méthodes pour effectuer un parcours de la pile à l’aide du fichier PDB.

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

Conserve le contexte de la pile entre les appels de la méthode [IDiaFrameData :: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

Facilite le parcours de la pile à l’aide du fichier de base de données de débogage de programme (PDB).

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

Décrit les propriétés d’une instance de symbole.

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

Énumère une table de source de données DIA.

## <a name="related-sections"></a>Sections connexes
[Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)

Décrit les énumérations et les structures utilisées par les différentes interfaces du kit de développement logiciel (SDK) DIA.

[Constantes (Kit de développement logiciel Debug Interface Access)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

Décrit les constantes disponibles dans le kit de développement logiciel (SDK) DIA.

## <a name="see-also"></a>Voir aussi

- [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)