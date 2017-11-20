---
title: "Prend en charge d’instruction pour Visual Basic 6.0 | Documents Microsoft"
ms.date: 08/28/2017
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.openlocfilehash: bdfe33cac19d488bc7763f3c61c518093d8afffa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Prend en charge d’instruction pour Visual Basic 6.0 sur Windows


## <a name="executive-summary"></a>Rapport de synthèse

L’équipe Visual Basic est validée à la compatibilité de « It Just Works » pour les applications Visual Basic 6.0 sur les systèmes d’exploitation Windows pris en charge suivants : 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012, y compris R2
- Windows Server 2008, y compris R2

Objectif de l’équipe Visual Basic est que les applications Visual Basic 6.0 continuent à s’exécuter sur les versions de Windows prises en charge. Comme indiqué dans ce document, le runtime Visual Basic 6.0 de core prendra en charge pour la durée de vie complète des versions de Windows prises en charge, ce qui est de cinq ans de support standard, suivie de cinq ans de support étendu (http://support.microsoft.com/gp/lifepolicy). La barre de prise en charge sera limitée aux régressions graves et problèmes de sécurité critiques pour les applications existantes.

## <a name="technical-summary"></a>Résumé technique

Visual Basic 6.0 est composée de ces éléments clés :
- Visual Basic 6.0 IDE (environnement de développement intégré).
- Runtime de Visual Basic 6.0 : bibliothèques de base et moteur d’exécution utilisé pour exécuter les applications Visual Basic 6.0.
- Fichiers de Visual Basic 6.0 Runtime Extended : sélectionné les fichiers OCX du contrôle ActiveX, les bibliothèques et les outils fournis avec le support d’IDE et une version en ligne.

## <a name="the-visual-basic-60-ide"></a>Visual Basic 6.0 IDE

L’IDE Visual Basic 6.0 n’est plus pris en charge à partir du 8 avril 2008. En outre, les équipes Windows et Visual Basic testés IDE de Visual Basic 6.0 sur Windows Vista, Windows 7, Windows Server 2008, Windows 8 et Windows 8.1 pour comprendre et atténuer (le cas échéant) des problèmes de compatibilité sur les versions 32 bits de Windows (voir le [Windows 64 bits](#62-bit-windows) section ci-dessous pour plus d’informations sur les systèmes 64 bits). Cette annonce ne modifie pas la stratégie de prise en charge pour l’IDE.

## <a name="the-visual-basic-60-runtime"></a>Le runtime Visual Basic 6.0

Le runtime Visual Basic 6.0 est défini en tant que les fichiers binaires compilés à l’origine inclus dans la liste de redistribution pour Visual Basic 6.0. Ces fichiers ont été marquées comme distribuable dans la licence de Visual Basic 6.0 d’origine. Exemples de ces fichiers de la bibliothèque runtime Visual Basic 6.0 (`msvbvm60.dll`), contrôles (par exemple, `msflxgrd.ocx`), ainsi que le runtime prend en charge les fichiers pour les autres zones fonctionnelles principales (c'est-à-dire MDAC).

Le runtime est divisé en trois groupes :

- Prise en charge des fichiers exécutables--d’expédition dans le système d’exploitation

   Fichiers d’exécution clé Visual Basic 6.0, utilisés dans la plupart des scénarios d’application, sont fournis dans et pris en charge pour la durée de vie des versions de Windows prises en charge. Cette durée de vie est de cinq ans de support standard et de cinq ans de support étendu entre le moment où une version donnée de Windows est fourni. Ces fichiers ont été testées pour leur compatibilité dans le cadre de nos tests d’applications Visual Basic 6.0 s’exécutant sur les versions de Windows prises en charge. 

   > [!NOTE]
   > Toutes les versions de Windows prises en charge contiennent une liste de pratiquement identique de fichiers, et la configuration requise de package redistribuable pour les applications contenant ces fichiers doit-elle être pratiquement identique. Une différence majeure est que `TriEdit.dll` a été supprimé de Windows Vista et versions ultérieures.

- Prise en charge des fichiers d’exécution –-étendus des fichiers à distribuer avec votre application

   Cette liste étendue se compose de contrôles key, les bibliothèques et les outils qui sont installés à partir du support de l’IDE ou à partir de Microsoft.com à l’ordinateur de développement. En règle générale, l’IDE VB6 installé ces contrôles à l’ordinateur de développement par défaut. Le développeur doit toujours à redistribuer ces fichiers avec l’application. La version prise en charge des fichiers est disponible en ligne sur du Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927).

- Fichiers d’exécution non pris en charge

   Certains fichiers soit ont été retiré standard prennent en charge ou n’ont jamais été inclus dans le cadre de la redistribution du runtime (par exemple, ils ont été inclus dans le `\Tools` dossier sur le support de l’IDE pour prendre en charge les applications héritées VB4/Visual Basic 5, ou il s’agissait de contrôles tiers). Ces fichiers ne sont pas pris en charge sur Windows ; au lieu de cela, ils sont soumis à tout contrat de prise en charge s’applique au support qu’ils ont été fournis avec. Cela n’implique aucune garantie autour de prise en charge et de maintenance. Dans certains cas, les versions ultérieures de ces bibliothèques sont prises en charge. Vous trouverez ci-dessous des informations sur la compatibilité descendante ou la migration vers des versions prises en charge.

Pour obtenir des détails spécifiques sur les fichiers inclus dans chaque groupe de support, consultez le [Runtime définition](#runtime-definition) section ci-dessous.

## <a name="the-visual-basic-60-support-lifetime"></a>La durée de vie de prise en charge de Visual Basic 6.0

Prise en charge et/ou la copie des fichiers binaires du runtime Visual Basic 6.0 sur les versions de Windows prises en charge ne modifie pas la stratégie de prise en charge pour l’IDE de Visual Basic 6.0 ou l’IDE de Visual Studio 6.0 dans sa globalité. Ces produits sorti du support étendu le 8 avril 2008.

Vous trouverez plus d’informations sur la politique de support des produits Microsoft à http://support.microsoft.com/gp/lifepolicy. Dans le cadre de ce cycle de vie de prise en charge, Microsoft continue de prendre en charge le runtime Visual Basic 6.0 sur les versions de Windows prises en charge pour la durée de vie de prise en charge de ces systèmes d’exploitation. Par exemple, cela signifie que le runtime Visual Basic 6.0 sera être pris en charge sur Windows Server 2003 jusqu'à juin 2008 de Support standard et juin 2013 pour étendre la prise en charge.
Pour plus d’informations sur la politique de prise en charge ou pour connaître les options de support supplémentaires, visitez notre page de prise en charge à http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>Windows 64 bits

Fichiers d’exécution Visual Basic 6.0 sont 32 bits. Ces fichiers sont fournis dans 64 bits systèmes d’exploitation Windows référencé dans le tableau ci-dessous. composants et applications de VB6 32 bits sont pris en charge dans l’environnement d’émulation WOW uniquement. composants 32 bits doivent également être hébergés dans des processus d’application 32 bits.

L’IDE Visual Basic 6.0 n’a jamais été offerte par une version 64 bits native, ni l’IDE 32 bits a été pris en charge sur Windows 64 bits. Développement VB6 sur Windows 64 bits ou n’importe quelle architecture native autre que 32 bits n’est pas et ne sera pas pris en charge.

## <a name="windows-7"></a>Windows 7

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows 7 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows 7.

Le runtime VB6 sera distribué et sera pris en charge dans Windows 7 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits.

## <a name="windows-81"></a>Windows 8.1

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows 8.1 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows 8.1.

Le runtime VB6 sera distribué et sera pris en charge dans Windows 8.1 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits. Les développeurs peuvent considérer l’histoire de la prise en charge pour Windows 8.1 comme étant le même pour Windows 7.

## <a name="windows-10"></a>Windows 10

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows 10 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows 10.

Le runtime VB6 sera distribué et sera pris en charge dans Windows 10 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits. Les développeurs peuvent considérer l’histoire de la prise en charge pour Windows 10 comme étant le même pour Windows 8.1.

## <a name="windows-server-2008"></a>Windows Server 2008

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows Server 2008 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows Server 2008.

Le runtime VB6 sera distribué et sera pris en charge dans Windows Server 2008 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows Server 2008 R2 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows Server 2008 R2.

Le runtime VB6 sera distribué et sera pris en charge dans Windows Server 2008 R2 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits. Les développeurs peuvent considérer l’histoire de la prise en charge pour Windows Server 2008 R2 comme étant le même pour Windows Server 2008.

## <a name="windows-server-2012"></a>Windows Server 2012

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows Server 2012 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows Server 2012.

Le runtime VB6 sera distribué et sera pris en charge dans Windows Server 2012 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits. Les développeurs peuvent considérer l’histoire de la prise en charge pour Windows Server 2012 comme étant le même pour Windows Server 2008 R2.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows Server 2012 R2 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows Server 2012 R2.

Le runtime VB6 sera distribué et sera pris en charge dans Windows Server 2012 R2 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits. Les développeurs peuvent considérer l’histoire de la prise en charge pour Windows Server 2012 R2 comme étant identiques, car il s’agit de Windows Server 2012.

## <a name="windows-server-2016"></a>Windows Server 2016

Depuis la version initiale de cette instruction de prise en charge, le système d’exploitation Windows Server 2016 a été publié. Ce document a été mis à jour pour préciser la prise en charge de Microsoft pour VB6 sur Windows Server 2016.

Le runtime VB6 sera distribué et sera pris en charge dans Windows Server 2016 pour la durée de vie du système d’exploitation. Fichiers d’exécution Visual Basic 6.0 toujours 32 bits uniquement, et tous les composants doivent être hébergés dans des processus d’application 32 bits. Les développeurs peuvent considérer l’histoire de la prise en charge pour Windows Server 2016 comme étant le même pour Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Versions de système d’exploitation Windows prises en charge

Cette section fournit des informations supplémentaires concernant les systèmes d’exploitation qui offrent un niveau de prise en charge de VB6. 

|Système d’exploitation Windows|VB6 Pris en charge le Runtime</br>Fichiers dans Windows ont prise en charge ?|VB6 Prise en charge Rutime</br>Fichiers étendus</br>pour distribuer avec votre application prise en charge ?| VB6 IDE prend en charge ?|
|---|---|---|---|
|Windows 10, toutes les éditions 32 bits|Oui *|Oui *|Non|
|Windows 10, toutes les éditions 64 bits (WOW uniquement)|Oui * </br> les applications 32 bits qui exécutent uniquement dans WOW|Oui* </br> les applications 32 bits qui exécutent uniquement dans WOW|Non|
|Windows 8.1, toutes les éditions 32 bits|Oui *|Oui *|Non|
| Windows 8.1, toutes les éditions 64 bits (WOW uniquement)|Oui * </br> les applications 32 bits qui exécutent uniquement dans WOW|Oui* </br> les applications 32 bits qui exécutent uniquement dans WOW|Non|
|Windows 7, toutes les éditions 32 bits|Oui *|Oui *|Non|
|Windows 7, toutes les éditions 64 bits (WOW uniquement)|Oui * </br> les applications 32 bits qui exécutent uniquement dans WOW|Oui * </br> les applications 32 bits qui exécutent uniquement dans WOW|Non|
|Windows Server 2016, toutes les éditions 64 bits (WOW uniquement)|Oui* </br> les applications 32 bits qui exécutent uniquement dans WOW|Oui* </br> les applications 32 bits qui exécutent uniquement dans WOW|Non|
|Windows Server 2012 R2, toutes les éditions 64 bits (WOW uniquement)<br>Windows Server 2012, toutes les éditions 64 bits (WOW uniquement)|Oui* </br> les applications 32 bits qui exécutent uniquement dans WOW|Oui* </br> les applications 32 bits qui exécutent uniquement dans WOW|Non|
|Windows Server 2008 R2, x64 toutes les éditions (WOW uniquement)</br>Windows Server 2008, x64 toutes les éditions (WOW uniquement)|Oui * </br> les applications 32 bits qui exécutent uniquement dans WOW|Oui * </br> les applications 32 bits qui exécutent uniquement dans WOW|Non|
|Windows Server 2008, toutes les éditions 32 bits|Oui *|Oui *|Non|


> [!NOTE]
> &#42;  Prise en charge du runtime VB6 est limitée par le cycle de vie de prise en charge de Windows.  Par exemple, si la cible du système d’exploitation est en phase de support étendu, VB6 ne peut pas avoir un niveau de prise en charge supérieur de support étendu.  Le [feuille du cycle de vie de prise en charge de Windows](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) contient des informations de cycle de vie supplémentaires sur les versions de Windows précédentes et actuelle.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Utilisation du runtime Visual Basic 6.0 à l’intérieur de VBA et Office

Visual Basic pour Applications ou VBA est une technologie de distincte couramment utilisée pour l’automatisation de l’application et de macros à l’intérieur d’autres applications, généralement à l’intérieur d’applications Microsoft Office. VBA est fourni dans le cadre d’Office et par conséquent, la prise en charge de VBA est régie par la stratégie de prise en charge de Microsoft Office. Toutefois, il existe des situations où VBA est utilisé pour appeler ou d’héberger des contrôles et les fichiers binaires du runtime Visual Basic 6.0. Dans ce cas, Visual Basic 6.0 pris en charge les fichiers d’exécution dans le système d’exploitation et la liste de fichiers étendus sont également pris en charge lorsqu’il est utilisé à l’intérieur d’un environnement VBA pris en charge.

Pour les scénarios de runtime VB6 à prendre en charge à l’intérieur de VBA, toutes les conditions suivantes doivent être remplies :

- La version du système d’exploitation hôte pour le runtime Visual Basic est toujours prise en charge.
- La version de l’hôte d’Office pour VBA est toujours prise en charge.
- Le runtime en question sont toujours pris en charge.

## <a name="visual-basic-script-vbscript"></a>Script Visual Basic (VBScript)

VBScript n’est pas lié à Visual Basic 6.0 et cette instruction de prise en charge. Toutefois, VBScript est actuellement prévu pour fonctionner en tant que partie de Windows 7, Windows 8.1, Windows 10, Windows Server 2008, y compris R2, Windows Server 2012, y compris R2 et Windows Server 2016 et est régie par la politique de support du système d’exploitation.

## <a name="third-party-components"></a>Les composants tiers

Microsoft ne peut pas fournir de prise en charge pour les composants tiers, tels que les contrôles OCX/ActiveX. Les clients sont invités à contacter le fournisseur de contrôle d’origine pour plus d’informations sur la prise en charge pour ces composants.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Signaler des problèmes avec les applications Visual Basic 6.0 sous Windows

Les développeurs de la planification à utiliser Visual Basic 6.0 avec l’un des systèmes d’exploitation Windows répertoriés installez ce système d’exploitation et commencer à tester la compatibilité des applications à l’aide de tests d’acceptation application d’origine.

Si vous détectez un problème avec votre application Visual Basic 6.0 en cours d’exécution sur l’un des systèmes d’exploitation Windows répertoriés, veuillez suivre vos canaux de support standard pour signaler le problème.

## <a name="supported-and-shipping-in-windows"></a>Prise en charge et de livraison dans Windows

| | | | |
|---|---|---|---|
|ATL.dll|         msadcor.dll|     msorcl32.dll|   OLE2.dll|
|Asycfilt.dll|    Msadcs.dll|      Msvbvm60.dll|   Ole32.dll|
|Comcat.dll|      MSADDS.dll|      Msvcirt.dll|    Oleaut32.dll|
|Compobj.dll|     msaddsr.dll|     Msvcrt.dll|     Oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    Msvcrt40.dll|   Oledb32.dll|
|DCOMCNFG.exe|    msado15.dll|     in Mtxdm.dll|      oledb32r.dll|
|Dllhost.exe|     msador15.dll|    Mtxoci.dll|     oledlg.dll|
|Ds16gt.dll|      msadrh15.dll|    Odbc16gt.dll|   OLEPRO32.dll|
|ds32gt.dll|      MSCPXL32.dll|    ODBC32.dll|     olethk32.dll|
|Expsrv.dll|      msdadc.dll|      ODBC32GT.dll|   regsvr32.exe|
|hh.exe|          Msdaenum.dll|    Odbcad32.exe|   rpcns4.dll|
|Hhctrl.ocx|      Msdaer.dll|      Odbccp32.cpl|   Rpcrt4.dll|
|Imagehlp.dll|    MSDAORA.dll|     Odbccp32.dll|   Scrrun.dll|
|iprop.dll|       msdaosp.dll|     ODBCCR32.dll|   Secur32.dll|
|Itircl.dll|      Msdaprst.dll|    Odbccu32.dll|   simpdata.tlb|
|Itss.dll|        MSDAPS.dll|      odbcint.dll|    SQLOLEDB.dll|
|Mfc40.dll|       MSDASC.dll|      odbcji32.dll|   Sqlsrv32.dll|
|Mfc42.dll|       MSDASQL.dll n'|     Odbcjt32.dll|   Stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   Stdole32.tlb|
|Msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   Storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    VBAJET32.dll|
|msadcf.dll|      MSDFMAP.dll|     odfox32.dll|    Vfpodbc.dll|
|msadcfr.dll|     MSDFMAP.ini|     odpdx32.dll|                |
|Msadco.dll|      module Msjtes40.dll|    Odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>Fichiers de prise en charge runtime à distribuer avec votre application

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |Msdbrptr.dll  |MSstdfmt.dll| 
|Comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |MSSTKPRP.dll| 
|Comctl32.ocx |Mschrt20.ocx |mshflxgd.ocx  |Mswcrun.dll|  
|Comdlg32.ocx |Mscomct2.ocx |mshtmpgr.dll  |Mswinsck.ocx| 
|dbadapt.dll  |Mscomctl.ocx |MSINET.ocx    |picclp32.ocx| 
|dbgrid32.ocx |Mscomm32.ocx |Msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |Msdatgrd.ocx |MSMask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |TABCTL32.ocx| 
|msadodc.ocx  |msdatrep.ocx |Msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>Non pris en charge, mais les mises à jour ou les mises à jour prises en charge et compatibles sont disponibles

| | | | |
|---|---|---|---|
|Dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|Mdac_typ.exe| msexcl35.dll| msjtor35.dll| Mstext35.dll|
|MSChart.ocx|  Msjet35.dll|  msltus35.dll| Msxbse35.dll|
|msdaerr.dll|  msjint35.dll| Mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  MSjt4jlt.dll| MSRD2X35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>Fichiers d’exécution non pris en charge

| | | | |
|---|---|---|---|
|ANIBTN32.ocx| SPIN32.ocx|   Rpcltscm.dll|  RDOCURS.dll|
|GRAPH32.ocx|  GAUGE32.ocx|  rpcmqcl.dll|   vbar332.dll|
|KEYSTA32.ocx| gswdll32.dll| rpcmqsvr.dll|  Visdata.exe|
|AUTMGR32.exe| Ciscnfg.exe|  Rpcss.exe|     vsdbflex.srg|
|AUTPRX32.dll| olecnv32.dll| établir|  THREED32.ocx|
|RACMGR32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|RACREG32.dll| rpcltc5.dll|  WindbVer.exe|  partir de tlbinf32.dll|
|GRID32.ocx|   rpcltccm.dll| msderun.dll|   TriEdit.dll|
|MSOUTL32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>Fichiers binaires de prise en charge de localisation

Les fichiers binaires suivants sont nécessaires pour prendre en charge les applications Visual Basic 6.0 en cours d’exécution sur les versions localisées du système d’exploitation Windows. Ils sont pris en charge, mais ne sont pas fournis avec Windows. Ces fichiers sont requis pour être livré avec l’installation de votre application.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>Fichiers de prise en charge runtime à distribuer avec votre application

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

