---
title: 'Étape 4 : Exposer une API web à partir d’une application ASP.NET Core'
description: Ajoutez une API web à votre application web ASP.NET Core avec ce tutoriel vidéo et des instructions détaillées.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 93e3b0af04060c3a3805b29e5d1da71c4f60ec31
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018088"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Étape 4 : Exposer une API web à partir d’une application ASP.NET Core

Suivez ces étapes pour ajouter une API web à votre application ASP.NET Core.

_Regardez cette vidéo et suivez la procédure pour ajouter la prise en charge de l’API web à votre première application ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Ouvrir le projet

Ouvrez votre application ASP.NET Core dans Visual Studio 2019. L’application devrait déjà utiliser EF Core pour gérer vos types de modèles, suivant la configuration effectuée à [l’étape 3 de cette série de tutoriels](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Ajouter un contrôleur d’API

Cliquez avec le bouton droit sur le projet et ajoutez un dossier nommé *Api*. Ensuite, cliquez avec le bouton droit sur ce dossier et choisissez **Ajouter** > **Nouvel élément généré automatiquement**. Choisissez **Contrôleur d’API avec actions, à l’aide d’Entity Framework**. Maintenant, choisissez une classe de modèle existante et cliquez sur **Ajouter**.

![Visual Studio 2019 – Contrôleur d’API généré automatiquement ASP.NET Core](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Examiner le contrôleur généré

Le code généré comporte une nouvelle classe de contrôleur. En haut de la définition de la classe se trouvent deux attributs.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Le premier spécifie que l’itinéraire des actions de ce contrôleur est `api/[controller]`, ce qui signifie que, si le contrôleur se nomme `GamesController`, l’itinéraire sera `api/Games`.

Le deuxième attribut, `[ApiController]`, ajoute quelques validations utiles à la classe, par exemple celle qui consiste à vérifier que chaque méthode d’action comporte son propre attribut `[Route]`.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Le contrôleur utilise le `AppDbContext` existant, passé à son constructeur. Chaque action aura recours à ce champ pour travailler avec les données de l’application.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

La première méthode est une requête GET simple, spécifiée avec l’attribut `[HttpGet]`. Elle n’accepte aucun paramètre et retourne la liste de tous les jeux de la base de données.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

La méthode suivante spécifie `{id}`, qui sera ajouté après `/` dans l’itinéraire ; l’itinéraire complet se présentera ainsi sous la forme `api/Games/5`, comme l’indique le commentaire en haut. L’entrée `id` est mappée avec le paramètre `id` dans la méthode. À l’intérieur de la méthode, si le modèle n’est pas valide, un résultat `BadRequest` est retourné. Sinon, EF tentera de trouver l’enregistrement correspondant à la valeur `id` fournie. En cas d’échec, un résultat `NotFound` est retourné, sinon l’enregistrement `Game` correspondant est retourné.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Ensuite, une demande `[HttpPut]` est envoyée à l’API pour effectuer des mises à jour. Le nouvel enregistrement `Game` est fourni dans le corps de la demande. Une étape de validation et de vérification des erreurs est effectuée : si tout réussit, l’enregistrement dans la base de données est mis à jour avec les valeurs fournies dans le corps de la demande. Sinon, une réponse d’erreur appropriée est retournée.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Une demande `[HttpPost]` est utilisée pour ajouter de nouveaux enregistrements au système. Comme avec `[HttpPut]`, l’enregistrement est ajouté dans le corps de la demande. S’il est valide, EF Core l’ajoute à la base de données et l’action retourne l’enregistrement mis à jour (avec son ID généré par la base de données) et le lien de l’enregistrement dans l’API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Enfin, un itinéraire `[HttpDelete]` est utilisé avec un ID pour supprimer un enregistrement. Si la demande est valide et qu’il existe un enregistrement portant l’ID spécifié, EF Core le supprime de la base de données.

## <a name="adding-swagger"></a>Ajouter Swagger

Swagger est un outil de test et de documentation d’API qui peut être ajouté sous la forme d’un ensemble de services et d’intergiciels (middleware) à une application ASP.NET Core. Pour cela, cliquez avec le bouton droit sur le projet et choisissez **Gérer les packages NuGet**. Cliquez sur **Parcourir**, recherchez `Swashbuckle.AspNetCore` et installez le package correspondant.

![Visual Studio 2019 – Ajouter Swashbuckle à partir de NuGet](media/vs-2019/vs2019-nuget-swashbuckle.png)

Après l’installation, ouvrez `Startup.cs` et ajoutez le code suivant à la fin de la méthode `ConfigureServices` :

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Vous devrez également ajouter `using Swashbuckle.AspNetCore.Swagger;` en haut du fichier.

Ensuite, ajoutez le code suivant à la méthode `Configure`, juste avant `UseMvc` :

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Vous devriez maintenant pouvoir générer et exécuter votre application. Dans le navigateur, accédez à `/swagger` dans la barre d’adresses. La liste des modèles et des points de terminaison d’API de votre application devrait apparaître. 

![Visual Studio 2019 – Page Swagger dans le navigateur](media/vs-2019/vs2019-swagger-browser.png)

Cliquez sur un point de terminaison sous Games, puis sur `Try it out` et `Execute` pour voir comment se comportent les différents points de terminaison.

## <a name="next-steps"></a>Étapes suivantes

Dans la vidéo suivante, vous allez apprendre à déployer votre application sur Azure.

[Étape 5 : Déployer une application ASP.NET Core sur Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec Swashbuckle et ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [Pages d’aide d’API web ASP.NET Core avec Swagger/OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)