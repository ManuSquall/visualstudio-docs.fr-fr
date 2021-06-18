---
title: Interruption des modifications d’API dans Visual Studio 2022 preview
description: En savoir plus sur les modifications d’API qui entraînent l’échec de la compilation des extensions VS existantes lors de la migration des extensions vers Visual Studio 2022 preview.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308732"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Interruption des modifications d’API dans Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Si vous migrez une extension vers Visual Studio 2022, les modifications avec rupture répertoriées ici peuvent vous affecter.

## <a name="reference-assemblies-no-longer-installed"></a>Les assemblys de référence ne sont plus installés

La plupart des assemblys que vous avez référencés et résolus par MSBuild à partir d’un répertoire d’installation de Visual Studio ne sont plus installés. Vous devez utiliser NuGet pour acquérir les assemblys de référence du kit de développement logiciel (SDK) Visual Studio dont vous avez besoin. Pour plus d’informations sur cette procédure, consultez [Modern Projects](update-visual-studio-extension.md#modernize-your-vsix-project) .

## <a name="removed-apis"></a>API supprimées

Dans Visual Studio 2022, un certain nombre d’API ont été supprimées dans le cadre du déplacement de Visual Studio vers l’avant. Vous trouverez une liste des API supprimées dans la page [liste des API supprimées](removed-api-list.md) .

## <a name="interop-breaking-changes"></a>Modifications avec rupture d’interopérabilité

La plupart de nos API ont été modifiées dans Visual Studio 2022, en général avec des modifications simples qui sont simples à prendre en compte pour votre code.

Pour gérer les modifications avec rupture, nous envisageons de fournir un nouveau mécanisme de distribution des assemblys d’interopérabilité. Plus précisément, pour Visual Studio 2022 et au-delà, nous fournissons un assembly d’interopérabilité unique avec des définitions pour de nombreuses interfaces Visual Studio publiques courantes. Cet assembly contient des définitions managées pour de nombreuses interfaces Visual Studio qui se déplacent de plusieurs assemblys d’interopérabilité. Le nouvel assembly d’interopérabilité est distribué via le `Microsoft.VisualStudio.Interop` package NuGet.

Toutefois, les composants Visual Studio qui sont principalement utilisés dans les contextes natifs et ont un faible nombre de modifications avec rupture continuent à avoir leurs propres assemblys d’interopérabilité (par exemple, l’assembly du débogueur sera toujours VisualStudio.Debugger.Interop.dll comme il le fait aujourd’hui). Dans tous les cas, les assemblys peuvent être référencés à partir de votre application, comme c’est le cas aujourd’hui.

Il s’agit d’une modification significative qui signifie que les extensions qui utilisent des API dans et un assembly créé dans cette nouvelle approche ne sont pas compatibles avec les versions antérieures de Visual Studio à l’aide de l’assembly d’interopérabilité précédent.

Cela présente quelques avantages très importants qui faciliteront la mise à jour de votre extension vers Visual Studio 2022 :

- Toute API cassée deviendra des erreurs de génération, ce qui les rendra plus faciles à trouver et à corriger.
- Vous devez uniquement mettre à jour le code qui utilise une API qui a été interrompue dans Visual Studio 2022.
- Vous ne serez pas en mesure d’utiliser accidentellement l’ancienne API rompue.

Globalement, ces modifications entraînent une version plus stable de Visual Studio pour tous les utilisateurs. Le principal inconvénient de cette approche est que vos assemblys managés ne pourront pas s’exécuter dans Visual Studio 2019 et Visual Studio 2022 sans compiler votre code une fois pour chaque version cible de Visual Studio.

À mesure que vous utilisez des erreurs de compilation en raison des différences d’API entre Visual Studio 2019 et Visual Studio 2022, vous pouvez trouver l’API ou le modèle que vous recherchez ci-dessous, avec des conseils sur la façon de le résoudre.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` ou `uint` où `IntPtr` est attendu

Nous pensons qu’il s’agit d’une erreur très courante. Pour faire en sorte que Visual Studio 2022 un processus de 64 bits, certaines de nos API d’interopérabilité devaient être corrigées là où il était supposé qu’un pointeur pouvait tenir dans un entier de 32 bits pour utiliser en fait une valeur de taille pointeur.

Exemple de l’erreur :

> Argument 3 : impossible de convertir de’out uint’en’out System. IntPtr'

Il vous suffit de mettre à jour votre code pour qu’il s’attende ou fournisse ou s’il `IntPtr` `UIntPtr` `int` `uint` est utilisé pour résoudre le saut.

Exemple de correctif :

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>Type Interop défini dans deux assemblys

Quand le compilateur C# signale une erreur indiquant qu’un type que vous utilisez est défini dans deux assemblys, vous référencez probablement un assembly à partir de la version Visual Studio 2019 du kit de développement logiciel (SDK) que vous ne devez plus référencer.

Exemple de l’erreur :

> erreur CS0433 : le type « IVsDpiAware » existe à la fois dans « Microsoft. VisualStudio. Interop, version = 17.0.0.0, culture = neutral, PublicKeyToken = b03f5f7f11d50a3a » et dans « Microsoft. VisualStudio. Shell. Interop. 16. DesignTime, version = 16.0.0.0, culture = neutral, PublicKeyToken = b03f5f7f11d50a3a »

Reportez-vous à notre [table de remappage d’assembly de référence](migrated-assemblies.md) pour voir quel nom d’assembly est le nom par défaut dans Visual Studio 2022.
En prenant en compte les deux assemblys nommés dans l’exemple d’erreur ci-dessus et en examinant cette table, vous remarquerez que `Microsoft.VisualStudio.Interop` est le nouveau nom de l’assembly. Le correctif consiste alors à supprimer la référence à `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` du projet.

Dans certains cas, nous proposons un package Visual Studio 2022 avec version pour l’assembly déconseillé qui contient des redirecteurs de type. Lorsque cette option est disponible, vous avez la possibilité de *mettre à niveau* votre référence de package vers la version Visual Studio 2022 au lieu de la supprimer. Les redirecteurs de type résolvent l’erreur à partir du compilateur.

Gardez à l’esprit que ces références peuvent parfois provenir d’une référence de package transitif, et peuvent donc être plus difficiles à supprimer qu’une référence directe effectuée dans votre fichier projet. Dans ce cas, assurez-vous que toutes les références à vos packages directs utilisent les packages du kit de développement logiciel (SDK) Visual Studio 2022 eux-mêmes. Vous pouvez faire référence à *project.assets.js* pour identifier la chaîne de packages chargée de l’intégration de l’assembly déconseillé. La mise à jour d’une référence de package transitif vers une version de Visual Studio 2022 est aussi simple que l’installation en tant que référence directe.

Si vous ne pouvez pas modifier l’arborescence des dépendances (par exemple, parce qu’elle implique une dépendance tierce), vous pouvez ajouter une référence de package directe au package pré-Visual Studio 2022 et ajouter des `ExcludeAssets="compile"` métadonnées à cet `PackageReference` élément pour résoudre l’erreur du compilateur. Mais gardez à l’esprit qu’avec cette technique, votre extension peut conserver une dépendance sur un assembly pré-Visual Studio 2022 et votre extension peut ne pas fonctionner au moment de l’exécution.

### <a name="missing-reference-to-an-interop-assembly"></a>Référence manquante à un assembly d’interopérabilité

Lorsque vous référencez un assembly compilé sur le kit de développement logiciel (SDK) pré-Visual Studio 2022, vous pouvez obtenir une erreur concernant une référence d’assembly manquante.

Exemple de l’erreur :

> Erreur CS0012 le type’IVsTextViewFilter’est défini dans un assembly qui n’est pas référencé. Vous devez ajouter une référence à l’assembly’Microsoft. VisualStudio. TextManager. Interop, version = 7.1.40304.0, culture = neutral, PublicKeyToken = b03f5f7f11d50a3a'

À l’aide de la [table de remappage d’assembly de référence](migrated-assemblies.md), vous pouvez vérifier que l’assembly demandé n’est en fait pas un que vous devez avoir pour référencer.

Le meilleur correctif consiste à mettre à jour votre dépendance vers une version compilée avec le kit de développement logiciel (SDK) Visual Studio 2022 afin que l’assembly d’interopérabilité supprimé ne soit plus demandé par le compilateur.

Dans certains cas, nous proposons un package Visual Studio 2022 avec version pour l’assembly déconseillé qui contient des redirecteurs de type. Quand cette option est disponible, vous avez la possibilité d’ajouter une référence de package à la version Visual Studio 2022 du package obsolète afin que les redirecteurs de type résolvent l’erreur à partir du compilateur.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` est manquant

Il existe deux définitions de cette interface, dans deux espaces de noms. Une seule d’entre elles était destinée à la consommation gérée.

Espace de noms Visual Studio 2019 | Espace de noms Visual Studio 2022 | Usage prévu
--|--|--
Microsoft. VisualStudio. Shell. IAsyncServiceProvider | Microsoft. VisualStudio. Shell. IAsyncServiceProvider | Consommation de code managé
Microsoft. VisualStudio. Shell. Interop. IAsyncServiceProvider | Microsoft. VisualStudio. Shell. COMAsyncServiceProvider. IAsyncServiceProvider | interopérabilité de bas niveau uniquement

Si vous voyez une erreur concernant `IAsyncServiceProvider` , il *se peut* que vous utilisiez celui prévu pour le code natif (la deuxième ligne).
Dans ce cas, vous pouvez mettre à jour vers le nouvel espace de noms ou basculer vers l’interface plus conviviale et gérée.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` et les `_DTE` échecs de conversion de type

`DTE` et `_DTE` sont deux interfaces. L’un est dérivé de l’autre. Toutefois, dans Visual Studio 2022, les types de base et dérivés sont permutés.
Cela fait échouer certaines assignations ou casts de type.

Cela signifie également que vous avez utilisé pour utiliser `new DTE()` , vous devez maintenant utiliser `new _DTE()` .

### <a name="missing-argument-on-a-method-invocation"></a>Argument manquant dans un appel de méthode

Certaines méthodes ne déclarent plus les arguments par défaut pour ce qui étaient des paramètres facultatifs dans l’API d’interopérabilité.
Si vous recevez une erreur concernant un argument manquant pour un appel de COM Interop, et que le paramètre appelle pour un `object` type, la valeur par défaut précédente que l’API d’interopérabilité Visual Studio 2019 définie peut avoir été `""` , pensez `""` à ajouter comme argument pour résoudre l’erreur de compilation.

En cas de doute sur l’utilisation de l’argument par défaut, essayez de basculer votre contexte de service de langage de Visual Studio 2022 vers Visual Studio 2019 afin d’obtenir IntelliSense avec les assemblys d’interopérabilité les plus anciens pour voir l’argument par défaut, puis ajoutez-le explicitement à votre code. Elle continuera de fonctionner correctement lorsqu’elle est compilée pour Visual Studio 2019, mais compilera maintenant pour Visual Studio 2022.

Exemple de correctif :

```diff
-process4.Attach2();
+process4.Attach2("");
```
