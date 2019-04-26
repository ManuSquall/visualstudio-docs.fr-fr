---
title: Générer, page du Concepteur de projet (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 99fb00ded29b9d0764f04d5062a7ee971954fbf7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433766"
---
# <a name="build-page-project-designer-c"></a>Générer, page du Concepteur de projets (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la page **Générer** du **Concepteur de projet** pour spécifier les propriétés de configuration de build du projet. Cette page s’applique uniquement aux projets [!INCLUDE[csprcs](../../includes/csprcs-md.md)].  
  
 Pour accéder à la page **Générer**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Ensuite, choisissez **Projet**, **Propriétés** dans la barre de menus. Quand le Concepteur de projet s’affiche, cliquez sur l’onglet **Générer**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Configuration et Plateforme  
 Les options suivantes vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.  
  
> [!NOTE]
> Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Par conséquent, ces options ne sont pas affichées. Pour plus d’informations, consultez [Configurations de projet Debug et Release](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Configuration**  
 Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres peuvent être **Active (Debug)** (valeur par défaut), **Debug**, **Release** ou **Toutes les configurations**.  
  
 **Plateforme**  
 Spécifie les paramètres de plateforme à afficher ou à modifier. Le paramètre par défaut est **Active (Any CPU)**. Vous pouvez modifier la plateforme active à l’aide du **Gestionnaire de configurations**. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="general"></a>Général  
 Les options suivantes vous permettent de configurer plusieurs paramètres du compilateur C#.  
  
 **Symboles de compilation conditionnelle**  
 Spécifie les symboles sur lesquels effectuer la compilation conditionnelle. Séparez les symboles par un point-virgule (";"). Pour plus d’informations, consultez [/define (options du compilateur C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).  
  
 **Définir la constante DEBUG**  
 Définit DEBUG comme symbole dans tous les fichiers de code source de votre application. Sélectionner cette option équivaut à utiliser l’option de ligne de commande `/define:DEBUG`.  
  
 **Définir la constante TRACE**  
 Définit TRACE comme symbole dans tous les fichiers de code source de votre application. Sélectionner cette option équivaut à utiliser l’option de ligne de commande `/define:TRACE`.  
  
 **Unité centrale cible**  
 Spécifie le processeur devant être ciblé par le fichier de sortie. Choisissez **x86** pour tout processeur compatible Intel 32 bits ; choisissez **x64** pour tout processeur compatible Intel 64 bits ; choisissez **ARM** pour les processeurs ARM ; ou choisissez **Any CPU** pour spécifier que tout processeur est acceptable. **Any CPU** est la valeur par défaut pour les projets, car elle permet l’exécution de l’application sur la plus large gamme de matériel.  
  
 Pour plus d’informations, consultez [/platform (options du compilateur C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).  
  
 **Préférer 32 bits**  
 Si la case **Préférer 32 bits** est cochée, l’application s’exécute comme une application 32 bits sur les versions 32 bits et 64 bits de Windows. Si elle est décochée, l’application s’exécutera comme une application 32 bits sur les versions 32 bits de Windows et comme une application 64 bits sur les versions 64 bits de Windows.  
  
 Si vous exécutez une application comme une application 64 bits, la taille du pointeur double, et des problèmes de compatibilité peuvent se produire avec d’autres bibliothèques qui sont exclusivement de type 32 bits. Il est utile d’exécuter une application 64 bits uniquement si elle a plus besoin de 4 Go de mémoire ou si les instructions 64 bits apportent une amélioration significative des performances.  
  
 Cette case à cocher est disponible uniquement si toutes les conditions suivantes ont remplies :  
  
- Dans la **page Générer**, la liste **Plateforme cible** a la valeur **Any CPU**.  
  
- Dans la **page Application**, la liste **Type de sortie** spécifie que le projet est une application.  
  
- Dans la **page Application**, la liste **Framework cible** spécifie .NET Framework 4.5.  
  
  **Autoriser les blocs de code unsafe**  
  Autorise la compilation du code utilisant le mot clé [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Pour plus d’informations, consultez [/unsafe (options du compilateur C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).  
  
  **Optimiser le code**  
  Active ou désactive les optimisations effectuées par le compilateur pour réduire la taille de votre fichier de sortie, et le rendre plus rapide et plus efficace. Pour plus d’informations, consultez [/optimize (options du compilateur C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 Les paramètres suivants sont utilisés pour configurer les options d’erreur et d’avertissement du processus de génération.  
  
 **Niveau d’avertissement**  
 Spécifie le niveau d’affichage pour les avertissements du compilateur. Pour plus d’informations, consultez [/warn (options du compilateur C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).  
  
 **Supprimer les avertissements**  
 Empêche le compilateur de générer un ou plusieurs avertissements. Séparez les numéros des avertissements par une virgule ou un point-virgule. Pour plus d’informations, consultez [/nowarn (options du compilateur C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).  
  
## <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs  
 Les paramètres suivants sont utilisés pour spécifier quels avertissements sont traités comme des erreurs. Sélectionnez l’une des options suivantes pour indiquer dans quelles circonstances retourner une erreur quand la génération rencontre un avertissement. Pour plus d’informations, consultez [/warnaserror (options du compilateur C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).  
  
 **Aucun**  
 Ne considère aucun avertissement comme une erreur.  
  
 **Avertissements spécifiques**  
 Considère les avertissements spécifiés comme des erreurs. Séparez les numéros des avertissements par une virgule ou un point-virgule.  
  
 **Tous**  
 Considère tous les avertissements comme des erreurs.  
  
## <a name="output"></a>Sortie  
 Les paramètres suivants sont utilisés pour configurer les options de sortie pour le processus de génération.  
  
 **Chemin de sortie**  
 Spécifie l'emplacement des fichiers de sortie pour cette configuration de projet. Entrez le chemin de la sortie de la génération dans cette zone ou choisissez sur le bouton **Parcourir** pour spécifier un chemin. Notez que ce chemin est relatif ; si vous entrez un chemin absolu, il sera enregistré comme relatif. Le chemin par défaut est bin\Debug ou bin\Release\\. Pour plus d’informations, consultez [Configurations de projet Debug et Release](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 Grâce aux configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou Release. Si vous cliquez sur la commande **Générer** dans le menu **Déboguer** (F5), la génération est placée dans l’emplacement de débogage, indépendamment du **Chemin de sortie** spécifié. Toutefois, avec la commande **Générer** du menu **Générer**, elle est placée dans l’emplacement spécifié. Pour plus d’informations, consultez [Configurations de projet Debug et Release](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Fichier de documentation XML**  
 Spécifie le nom d’un fichier dans lequel les commentaires de la documentation seront traités. Pour plus d’informations, consultez [/doc (options du compilateur C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).  
  
 **Inscrire pour COM Interop**  
 Indique que votre application managée exposera un objet COM (un wrapper CCW) qui permet à un objet COM d’interagir avec votre application managée. La propriété **Type de sortie** de la [page Application](../../ide/reference/application-page-project-designer-visual-basic.md) du **Concepteur de projet** pour cette application doit avoir la valeur **Bibliothèque de classes** pour que la propriété **Inscrire pour COM Interop** soit disponible. Pour obtenir un exemple de classe que vous pouvez inclure dans votre application [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et exposer en tant qu’objet COM, consultez [Exemple de classe COM](http://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).  
  
 **Générer un assembly de sérialisation**  
 Spécifie si le compilateur utilisera l’outil XML Serializer Generator (Sgen.exe) pour créer des assemblys de sérialisation XML. Les assemblys de sérialisation peuvent améliorer les performances de démarrage de <xref:System.Xml.Serialization.XmlSerializer> si vous avez utilisé cette classe pour sérialiser les types dans votre code. Par défaut, cette option a la valeur **Auto**, qui spécifie que les assemblys de sérialisation ne peuvent être générés que si vous avez utilisé <xref:System.Xml.Serialization.XmlSerializer> pour encoder les types dans votre code en XML. **Inactif** spécifie que les assemblys de sérialisation ne doivent jamais être générés, que votre code utilise <xref:System.Xml.Serialization.XmlSerializer> ou non. **Actif** spécifie que les assemblys de sérialisation doivent toujours être générés. Les assemblys de sérialisation sont appelés `TypeName`.XmlSerializers.dll. Pour plus d’informations, consultez [Outil XML Serializer Generator (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
 **Avancé**  
 Cliquez pour afficher la [boîte de dialogue Paramètres de génération avancés (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)   
 [Options du compilateur C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)
