---
title: Modification de feuilles de style XSLT
description: Découvrez les fonctionnalités de l’éditeur XML permettant de modifier les feuilles de style XSLT, notamment la coloration de la syntaxe, les soulignements et le lancement du débogueur XSLT à partir de l’éditeur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: df9bff28e68b373bb932f33ff8fb34439f0b4e7c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969086"
---
# <a name="edit-xslt-style-sheets"></a>Modification des feuilles de style XSLT

L’éditeur XML peut également être utilisé pour modifier des feuilles de style XSLT. Vous pouvez ainsi tirer profit des fonctionnalités par défaut de l’éditeur telles qu’IntelliSense, mode plan, extraits XML, etc. Des nouvelles fonctionnalités facilitent en outre le développement en XSLT.

## <a name="xslt-features"></a>Fonctionnalités XSLT

Le tableau suivant décrit les fonctions spécifiques à la manipulation des feuilles de style XSLT.

**Coloration de la syntaxe**

Les mots clés XSLT, tels que `template` et `match` , sont affichés dans la couleur de mot clé XSLT spécifiée par les paramètres des **polices et des couleurs** .

**Traits de soulignement ondulés**

L’éditeur XML utilise le fichier *XSLT. xsd* installé pour valider les feuilles de style XSLT. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. L’éditeur XML compile également la feuille de style en arrière-plan et signale les erreurs ou avertissements du compilateur avec des soulignements ondulés appropriés.

**Prise en charge des blocs de script**

Le code placé dans des blocs de script est pris en charge par le débogueur XSLT ; vous pouvez donc définir des points d'arrêt et effectuer une exécution pas à pas dans le code du bloc de script.

**Affichage de la sortie XSLT**

Vous pouvez exécuter une transformation XSL et afficher la sortie de l’éditeur XML. Pour plus d’informations, consultez [procédure : exécution d’une transformation XSLT à partir de l’éditeur XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Débogage XSLT**

Vous pouvez lancer le débogueur XSLT à partir d’un fichier XSLT dans l’éditeur XML. Le débogueur prend en charge la définition de points d'arrêt dans le fichier XSLT, l'affichage de l'état d'exécution de XSLT, etc. Lorsque le pointeur est placé sur une variable XSLT, une info-bulle apparaît et affiche la valeur de la variable. Le débogueur peut permettre de déboguer une feuille de style ou une transformation XSLT compilée invoquée depuis une autre application. Pour plus d’informations, consultez [débogage XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
