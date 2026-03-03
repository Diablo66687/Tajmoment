# TajMoment.cz

**Univerzální platforma pro sdílení přání a koordinaci darů**

![.NET 8](https://img.shields.io/badge/.NET-8.0-512BD4)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-MVC-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Tests](https://img.shields.io/badge/Tests-44%2B-brightgreen)

## 🎯 O Projektu

TajMoment.cz je moderní webová aplikace pro koordinaci darů a správu wishlistů pro různé příležitosti. Ideální pro tajného Santa, svatby, narozeniny, baby shower a mnoho dalšího!

### ✨ Hlavní Funkce

- 🔒 **Bezpečná autentizace** - ASP.NET Core Identity s validací hesel
- 👥 **Soukromé skupiny** - Uzavřené skupiny s pozváním (pozvánkové kódy a tokeny)
- 🎁 **Wishlisty** - Každý člen si vytvoří seznam přání s kategoriemi
- 💬 **Real-time chat** - SignalR pro komunikaci bez vědomí obdarovaného
- 📅 **12 typů událostí** - Od narozenin po Vánoce
- 📱 **Responzivní design** - Funguje na mobilu, tabletu i desktopu
- 🎨 **Moderní UI** - Přátelský a intuitivní interface s Bootstrap 5
- ✅ **Unit testy** - 44+ komprehenzivních testů (xUnit, Moq)

## 🛠️ Technologie

| Komponenta | Technologie |
|------------|------------|
| **Framework** | ASP.NET Core 8.0 MVC |
| **Databáze** | Entity Framework Core 8.0 + SQL Server |
| **Frontend** | Bootstrap 5, Font Awesome 6, CSS3 |
| **Autentizace** | ASP.NET Core Identity |
| **Real-time** | SignalR |
| **Testování** | xUnit, Moq |
| **Jazyk** | C# 12.0 |

## 📊 Architektura

### Databázové Modely

| Model | Popis |
|-------|-------|
| `ApplicationUser` | Rozšířený uživatelský model (Identity) |
| `Group` | Skupiny pro různé události |
| `GroupMember` | Členství ve skupině s rolí (Admin, Member) |
| `Wishlist` | Wishlist na uživatele v rámci skupiny |
| `WishlistItem` | Jednotlivé položky s cenou, kategorií, rezervací |
| `Message` | Zprávy v chatu skupiny (s replies) |
| `GroupInvitation` | Pozvánky s tokeny a stavem (Pending, Accepted, Declined) |

### Kategorie Položek

Electronics • Clothing • Books • Toys • HomeDecor • Beauty • Sports • Food • Experiences • Jewelry • Other

### Typy Událostí

🎄 Vánoce • 🎅 Tajný Santa • 💒 Svatba • 🎂 Narozeniny • 💑 Výročí • 👶 Baby Shower • 🏠 Novinky do bytu • 🎓 Promoce • 💕 Valentýn • 👩 Den matek • 👨 Den otců • 🎉 Jiné

## 🚀 Instalace a Spuštění

### Požadavky

- .NET 8 SDK (nebo vyšší)
- SQL Server (LocalDB nebo plná verze)
- Visual Studio 2022 / VS Code / JetBrains Rider

### Krok za krokem

**1. Klonování repository**
```bash
git clone https://github.com/Diablo66687/skrib.git
cd skrib/tajmoment.cz/tajmoment.cz
```

**2. Obnovení NuGet balíčků**
```bash
dotnet restore
```

**3. Nastavení connection stringu**

Upravte `appsettings.json`:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=TajMoment;Trusted_Connection=true;MultipleActiveResultSets=true"
  }
}
```

**4. Vytvoření a inicializace databáze**
```bash
dotnet ef database update
```

Nebo v Package Manager Console (Visual Studio):
```
Update-Database
```

**5. Spuštění aplikace**
```bash
dotnet run
```

**6. Otevřete prohlížeč**
```
https://localhost:7117
```

### 🎯 Demo Data

Aplikace se automaticky naplní testovacími daty při prvním spuštění! 

**Přihlašovací údaje (všechny účty mají stejné heslo: `Demo123!`):**
- `admin@tajmoment.cz` - Admin účet
- `jana.novakova@email.cz` - Demo uživatel
- `petr.svoboda@email.cz` - Demo uživatel
- `marie.dvorakova@email.cz` - Demo uživatel
- `tomas.horak@email.cz` - Demo uživatel

**Co najdete:**
- 🎂 3 ukázkové skupiny (Narozeniny, Tajný Santa, Svatba)
- 🎁 Wishlisty s položkami
- 💬 Chat zprávy
- ✅ Rezervované a zakoupené dárky
- 📧 Čekající pozvánky

📄 Detaily: [`DEMO_DATA.md`](./DEMO_DATA.md)

## 🔑 Autentizace a Bezpečnost

### Požadavky na heslo
- Minimálně 6 znaků
- Alespoň jedno velké písmeno
- Alespoň jedno malé písmeno
- Alespoň jednu číslici

### Pravidla
- Email musí být unikátní
- Potvrzení emailu: zatím vypnuté (doporučujeme pro produkci)
- Cookies s expirací 30 dnů (sliding expiration)

## 📖 Uživatelské Příručky

### Registrace a Přihlášení

1. Klikněte na **Registrace** v hlavním menu
2. Vyplňte email, uživatelské jméno a heslo
3. Přihlaste se přes **Přihlášení**

### Vytvoření Skupiny

1. Po přihlášení jděte na **Moje skupiny**
2. Klikněte na **Nová skupina**
3. Vyberte typ akce a přidejte členy
4. Sdílejte pozvánkový kód nebo odkaz

### Vytvoření Wishlistu

1. V rámci skupiny jděte na **Wishlisty**
2. Klikněte na **Nový wishlist**
3. Přidejte položky s cenou a kategorií
4. Ostatní mohou rezervovat nebo koupit

## 📁 Struktura Projektu

```
tajmoment.cz/
├── Controllers/              # MVC kontrolery
│   ├── AccountController.cs  # Registrace, přihlášení, profil
│   ├── DashboardController.cs
│   ├── GroupsController.cs
│   └── ...
├── Models/                  # Datové modely
│   ├── ApplicationUser.cs
│   ├── Group.cs
│   ├── ItemCategory.cs
│   └── ...
├── ViewModels/             # View modely pro formuláře
│   ├── LoginViewModel.cs
│   ├── RegisterViewModel.cs
│   └── ...
├── Views/                  # Razor views (.cshtml)
│   ├── Shared/_Layout.cshtml
│   ├── Account/
│   ├── Dashboard/
│   └── Home/
├── Data/                   # DbContext a migrace
│   ├── ApplicationDbContext.cs
│   └── Migrations/
├── wwwroot/               # Statické soubory
│   ├── css/
│   ├── js/
│   └── lib/
├── appsettings.json       # Konfigurace
├── Program.cs             # Startup
└── README.md              # Tato dokumentace

tajmoment.cz.Tests/        # Unit testy
├── Controllers/           # Controller testy
├── Models/               # Model testy
├── Validation/           # ViewModel testy
└── README.md             # Test dokumentace
```

## 🧪 Unit Testy

Projekt obsahuje **44+ unit testů** s vysokým pokrytím kritických funkcí.

### Spuštění Testů

**Visual Studio:**
```
Test → Test Explorer → Run All Tests
```

**Command Line:**
```sh
cd tajmoment.cz.Tests
dotnet test
```

**Specific Test:**
```sh
dotnet test --filter ClassName=AccountControllerTests
```

### Test Pokrytí

| Kategorie | Počet | Popis |
|-----------|-------|-------|
| **Models** | 18 | ItemCategory, EventType, GroupRole, Group, atd. |
| **ViewModels** | 13 | Validace Login, Register formulářů |
| **Controllers** | 13 | AccountController, DashboardController |
| **Celkem** | **44+** | ✅ Všechny projdou |

### Struktura Testů

```
tajmoment.cz.Tests/
├── Controllers/
│   ├── AccountControllerTests.cs    # 10 testů
│   └── DashboardControllerTests.cs  # 3 testy
├── Models/
│   ├── EventTypeTests.cs
│   ├── GroupRoleTests.cs
│   ├── GroupTests.cs
│   ├── InvitationStatusTests.cs
│   ├── ItemCategoryTests.cs
│   └── WishlistItemTests.cs
├── Validation/
│   ├── LoginViewModelTests.cs
│   ├── RegisterViewModelTests.cs
│   └── ViewModelValidationTests.cs
└── README.md
```

Detaily: [`tajmoment.cz.Tests/README.md`](./tajmoment.cz.Tests/README.md)

## 🔧 Vývoj

### Hot Reload During Development
```bash
dotnet watch run
```

### Databázové migrace

Při změně modelu:
```bash
dotnet ef migrations add MigrationName
dotnet ef database update
```

### Smazání databáze a reset
```bash
dotnet ef database drop
dotnet ef database update
```

## 📋 Konfigurační Soubory

### appsettings.json (Vývoj)
- LocalDB connection string
- Development logging level

### appsettings.Production.json (Doporučeno)
- Production SQL Server connection
- Bezpečné uložení tajemství (Key Vault)
- Optimalizované nastavení

## 📝 Ochrana Osobních Údajů a Právní Věci

- **Privacy Policy**: `/Home/Privacy` - Informace o zpracování osobních údajů
- **Podmínky Použití**: `/Home/Terms` - Pravidla používání služby

⚠️ **Důležité**: Texty na těchto stránkách jsou informativní. Před nasazením do produkce doporučujeme zkontrolovat s právníkem!

## 🌐 Produkční Nasazení

### Doporučené kroky

1. **Bezpečnost**
   - Zapnout potvrzení emailu
   - Nastavit bezpečné connection stringy
   - Nakonfigurovat HTTPS certifikáty
   - Přidat bezpečnostní hlavičky (HSTS, CSP)

2. **Monitoring**
   - Serilog pro strukturované logování
   - Application Insights pro monitorování
   - Email alerting pro kritické chyby

3. **Databáze**
   - Migrovat na production SQL Server
   - Nastavit zálohování
   - Optimalizovat indexy

4. **Cloud Hosting**
   - Azure App Service (doporučeno)
   - Docker container
   - Kubernetes (pro vyšší škálování)

## 🐛 Known Issues & TODO

- [ ] Email konfirmace - rozeslání potvrzovacích emailů
- [ ] Notifikace - push notifikace pro nové zprávy
- [ ] Plné SignalR integrace - chat bez obnovovaní
- [ ] Integration testy - pokrytí databáze
- [ ] Dark mode - přepínač mezi motivy
- [ ] GitHub Actions CI/CD - auto-build a testy

## 🤝 Příspěvky

Projekt je vytvořen jako portfolio projekt pro junior C# vývojáře. Příspěvky jsou vítány! Prosím vytvořte pull request s popisem změn.

## 📄 Licence

Projekt je pod licencí MIT - viz `LICENSE` soubor.

## 👨‍💻 Autor

**Vytvořil DevBrain** 🎨🚀

Více informací: [www.devbrain.cz](https://www.devbrain.cz)

## 📞 Kontakt a Podpora

- Email: [kontakt@tajmoment.cz](mailto:kontakt@tajmoment.cz)
- GitHub Issues: Hlašte bugy a návrhy
- GitHub: [github.com/Diablo66687/skrib](https://github.com/Diablo66687/skrib)

---

**Poslední aktualizace**: Prosinec 2025  
**Verze**: 1.0.0  
**Status**: Active Development 🚧  
**Test Coverage**: 44+ testů ✅  
**Build Status**: ✅ Passing
