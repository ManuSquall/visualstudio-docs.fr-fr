---
title: Considérations relatives à la sécurité lors de l’utilisation de données XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656136"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Considérations de sécurité lors de l'utilisation de données XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique présente les problèmes de sécurité à prendre en compte lors de l'utilisation de l'éditeur XML ou du débogueur XSLT.

## <a name="xml-editor"></a>Éditeur XML
 L'éditeur XML est basé sur l'éditeur de texte Visual Studio. Il repose sur les classes <xref:System.Xml> et <xref:System.Xml.Xsl> pour traiter la plupart des processus XML.

- Les transformations XSLT s'exécutent dans un nouveau domaine d'application. Les transformations XSLT sont en *mode bac à sable (sandbox)*; autrement dit, la stratégie de sécurité d’accès du code de votre ordinateur est utilisée pour déterminer les autorisations restreintes en fonction de l’emplacement de la feuille de style XSLT. Par exemple, les feuilles de style provenant d'un emplacement Internet ont les autorisations les plus limitées, tandis que les feuilles de style copiées vers votre disque dur s'exécutent en Confiance totale.

- La classe <xref:System.Xml.Xsl.XslCompiledTransform> permet de compiler le XSLT en un langage intermédiaire Microsoft afin d'accélérer l'exécution.

- Les schémas qui pointent vers un emplacement externe dans le fichier catalogue sont automatiquement téléchargés lors du chargement initial de l'éditeur XML. La classe <xref:System.Xml.Schema.XmlSchemaSet> permet de compiler les schémas. Le fichier catalogue fourni avec l'éditeur XML n'offre aucun lien vers des schémas externes. L'utilisateur doit ajouter explicitement une référence au schéma externe avant que l'éditeur XML télécharge le fichier de schéma. Le téléchargement HTTP peut être désactivé via la page **Outils divers options** de l’éditeur XML.

- L'éditeur XML utilise les classes <xref:System.Net> pour télécharger les schémas

## <a name="xslt-debugger"></a>Débogueur XSLT
 Le débogueur XSLT utilise le moteur de débogage managé Visual Studio et les classes des espaces de noms <xref:System.Xml> et <xref:System.Xml.Xsl>.

- Le débogueur XSLT exécute chaque transformation XSLT dans un domaine d'application en sandbox. La stratégie de sécurité d'accès au code de votre ordinateur permet de déterminer les autorisations limitées selon l'emplacement de la feuille de style XSLT. Par exemple, les feuilles de style provenant d'un emplacement Internet ont les autorisations les plus limitées, tandis que les feuilles de style copiées vers votre disque dur s'exécutent en Confiance totale.

- La feuille de style XSLT est compilée à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.

- L'évaluateur d'expression XSLT est chargé par le moteur de débogage managé. Ce dernier présume que tout le code est exécuté depuis l'ordinateur local de l'utilisateur. De même, la classe <xref:System.Xml.Xsl.XslCompiledTransform> télécharge le fichier XSLT sur l'ordinateur local de l'utilisateur. La possibilité d'élévation du privilège d'exécution est atténuée par le fait que toutes les transformations XSLT sont exécutées dans un nouveau domaine d'application dont les autorisations sont limitées.

## <a name="see-also"></a>Voir aussi
 [Domaines d'application](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)
