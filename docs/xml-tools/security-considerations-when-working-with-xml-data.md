---
title: Considérations de sécurité lors de l'utilisation de données XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e18d2c2e47c3cc1f7e1b3be0112e49e2710e45c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815836"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Considérations relatives à la sécurité lors de l’utilisation de données XML

Cette rubrique décrit les problèmes de sécurité que vous devez connaître lorsque vous utilisez l’éditeur XML ou le débogueur XSLT.

## <a name="xml-editor"></a>Éditeur XML

L’éditeur XML est basé sur l’éditeur de texte Visual Studio. Il repose sur les classes <xref:System.Xml> et <xref:System.Xml.Xsl> pour traiter la plupart des processus XML.

- Les transformations XSLT s'exécutent dans un nouveau domaine d'application. Les transformations XSLT sont en *mode bac à sable (sandbox)*; autrement dit, la stratégie de sécurité d’accès du code de votre ordinateur est utilisée pour déterminer les autorisations restreintes en fonction de l’emplacement de la feuille de style XSLT. Par exemple, les feuilles de style provenant d'un emplacement Internet ont les autorisations les plus limitées, tandis que les feuilles de style copiées vers votre disque dur s'exécutent en Confiance totale.

- La classe <xref:System.Xml.Xsl.XslCompiledTransform> permet de compiler le XSLT en un langage intermédiaire Microsoft afin d'accélérer l'exécution.

- Les schémas qui pointent vers un emplacement externe dans le fichier catalogue sont automatiquement téléchargés lors du premier chargement de l’éditeur XML. La classe <xref:System.Xml.Schema.XmlSchemaSet> permet de compiler les schémas. Le fichier catalogue fourni avec l’éditeur XML ne contient pas de liens vers des schémas externes. L’utilisateur doit ajouter explicitement une référence au schéma externe pour que l’éditeur XML télécharge le fichier de schéma. Le téléchargement HTTP peut être désactivé via la page **Outils divers options** de l’éditeur XML.

- L’éditeur XML utilise les <xref:System.Net> classes pour télécharger des schémas

## <a name="xslt-debugger"></a>débogueur XSLT

Le débogueur XSLT utilise le moteur de débogage managé Visual Studio et les classes des espaces de noms <xref:System.Xml> et <xref:System.Xml.Xsl>.

- Le débogueur XSLT exécute chaque transformation XSLT dans un domaine d'application en sandbox. La stratégie de sécurité d'accès au code de votre ordinateur permet de déterminer les autorisations limitées selon l'emplacement de la feuille de style XSLT. Par exemple, les feuilles de style provenant d'un emplacement Internet ont les autorisations les plus limitées, tandis que les feuilles de style copiées vers votre disque dur s'exécutent en Confiance totale.

- La feuille de style XSLT est compilée à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.

- L'évaluateur d'expression XSLT est chargé par le moteur de débogage managé. Ce dernier présume que tout le code est exécuté depuis l'ordinateur local de l'utilisateur. De même, la classe <xref:System.Xml.Xsl.XslCompiledTransform> télécharge le fichier XSLT sur l'ordinateur local de l'utilisateur. La possibilité d'élévation du privilège d'exécution est atténuée par le fait que toutes les transformations XSLT sont exécutées dans un nouveau domaine d'application dont les autorisations sont limitées.

## <a name="see-also"></a>Voir aussi

- [Domaines d’application](/dotnet/framework/app-domains/application-domains)