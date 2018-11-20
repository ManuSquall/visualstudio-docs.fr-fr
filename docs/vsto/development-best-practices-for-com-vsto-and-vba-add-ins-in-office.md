---
title: Meilleures pratiques de développement COM, VSTO et VBA des compléments dans Office
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f821b9769b9353fbee6379ddc1b3826f87ac2de
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671091"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Meilleures pratiques de développement COM, VSTO et VBA des compléments dans Office
  Si vous développez des compléments COM, VSTO ou de VBA pour Office, suivez les meilleures pratiques de développement décrits dans cet article.   Cela permet de s’assurer :

-  Compatibilité de vos compléments entre différentes versions et les déploiements de Microsoft Office.
-  Réduction de la complexité de déploiement de compléments pour vos utilisateurs et les administrateurs informatiques.
-  Échecs d’installation ou d’exécution involontaires de votre complément ne se produisent pas.

>Remarque : À l’aide de la [pont du bureau](/windows/uwp/porting/desktop-to-uwp-root) pour préparer votre COM, VSTO VBA complément ou pour le Windows Store n’est pas pris en charge. Compléments COM, VSTO et VBA ne peuvent pas être distribués dans le Windows Store ou de l’Office Store. 
  
## <a name="do-not-check-for-office-during-installation"></a>Ne pas vérifier Office pendant l’installation  
 Nous ne vous recommandons d’avoir votre complément détecter si Office est installé pendant l’installation du complément. Si Office n’est pas installé, vous pouvez installer le complément et l’utilisateur sera en mesure d’y accéder une fois Office installé. 
  
## <a name="use-embedded-interop-types-nopia"></a>Utiliser des Types Interop incorporés (NoPIA)  
Si votre solution utilise .NET 4.0 ou version ultérieure, utilisez des types interop incorporés (NoPIA) au lieu d’en fonction de l’Office assemblys PIA (Primary Interop) redistribuables. À l’aide de l’incorporation de type réduit la taille de l’installation de votre solution et garantit la compatibilité future. Office 2010 était la dernière version d’Office fourni l’assembly PIA redistribuable. Pour plus d’informations, consultez [procédure pas à pas : incorporation des informations de type provenant d’assemblys Microsoft Office](https://msdn.microsoft.com/library/ee317478.aspx) et [équivalence de Type et types interop incorporés](/windows/uwp/porting/desktop-to-uwp-root).

Si votre solution utilise une version antérieure de .NET, nous recommandons que vous mettez à jour votre solution pour utiliser .NET 4.0 ou version ultérieure. À l’aide de .NET 4.0 ou version ultérieure réduit les composants requis de runtime sur les versions plus récentes de Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Éviter en fonction des versions spécifiques d’Office  
Si votre solution utilise une fonction qui est uniquement disponible dans les versions plus récentes d’Office, vérifiez que la fonctionnalité existe (si possible, au niveau de fonctionnalité) lors de l’exécution (par exemple, à l’aide d’exception de gestion des exceptions ou en vérifiant la version). Valider les versions minimales, au lieu des versions spécifiques, à l’aide d’API prises en charge dans le modèle objet, tel que le [Application.Version propriété](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Nous ne recommandons pas s’appuient sur les métadonnées binaires Office, les chemins d’installation ou les clés de Registre, car ceux-ci peuvent changer entre des installations, des environnements et des versions.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Activer l’utilisation de Office 32 bits et 64 bits   
Votre cible de build par défaut doit prendre en charge les (x86) 32 bits et 64 bits (x64), sauf si votre solution dépend des bibliothèques qui sont uniquement disponibles pour un nombre de bits spécifique. L’augmentation de la version 64 bits d’Office dans l’adoption, en particulier dans les environnements big data. Prise en charge 32 bits et 64 bits rend plus facile pour vos utilisateurs pour effectuer la transition entre les versions 32 bits et 64 bits d’Office.

Lorsque vous écrivez du code VBA, utilisez 64 bits safe instructions declare et convertir des variables comme il convient. En outre, assurez-vous que les documents peuvent être partagées entre les utilisateurs qui exécutent des versions 32 bits ou 64 bits d’Office en fournissant le code pour chaque nombre de bits. Pour plus d’informations, consultez [64 bits de Visual Basic pour une vue d’ensemble des applications](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Prendre en charge les environnements restreints   
Votre solution ne doit pas nécessiter de privilèges d’élévation de compte d’utilisateur ou administrateur. En outre, la solution ne doit pas dépendre définition ou la modification :

- Le répertoire de travail actuel.
- Répertoires de chargement DLL.
- La variable de chemin d’accès.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modifier l’emplacement des données partagées et paramètres
Si la solution se compose d’un complément et un processus qui est externe à Office, n’utilisez pas le dossier application data de l’utilisateur ou le Registre pour échanger des données ou des paramètres entre le complément et le processus externe. Envisagez plutôt d’utiliser le dossier temporaire de l’utilisateur, de dossier de documents ou de répertoire d’installation de votre solution.

## <a name="increment-the-version-number-with-each-update"></a>Incrémenter le numéro de version avec chaque mise à jour
Définir le numéro de version des fichiers binaires dans votre solution et incrémenter avec chaque mise à jour. Cela rend plus facile pour les utilisateurs à identifier les modifications apportées entre les versions et évaluer la compatibilité.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fournir des instructions de prise en charge pour les dernières versions d’Office
Les clients demandent les éditeurs de logiciels pour fournir des instructions de prise en charge pour leurs COM, VSTO et VBA des compléments qui s’exécutent dans Office. Répertorier votre prise en charge explicite instructions aide les clients à l’aide d’Office 365 ProPlus outils de préparation comprennent votre prise en charge. 

Pour fournir des instructions de prise en charge pour les applications clientes Office (par exemple, Word ou Excel), vérifiez d’abord que vos compléments s’exécutent dans la version actuelle d’Office et validez ensuite à fournir des mises à jour si votre complément s’arrête dans une version ultérieure. Il est inutile de tester vos compléments lorsque Microsoft publie une nouvelle build ou une mise à jour pour Office. Microsoft change rarement la plate-forme d’extensibilité COM, VSTO et VBA dans Office, et ces modifications seront bien documentées.

>Important : Microsoft gère une liste des compléments pris en charge pour les rapports de compatibilité et les informations de contact d’éditeurs de logiciels indépendants. Pour obtenir votre complément répertorié, consultez [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Utiliser Process Monitor pour vous aider à déboguer l’installation ou le chargement des problèmes
Si votre complément présente des problèmes de compatibilité durant l’installation ou de la charge, ils peuvent être liés aux problèmes concernant l’accès de fichier ou du Registre. Utilisez [Process Monitor](/sysinternals/downloads/procmon) ou un outil de débogage similaire pour vous connecter et de comparer le comportement par rapport à un environnement de travail pour aider à identifier le problème.
