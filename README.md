<img src="assets/logo.png" width="112" height="112" alt="BetaUpdate logo">

# BetaUpdate

Update a Beta prior with Bernoulli counts. This Blyx library is part of the probability and causal analysis collection.

A point estimate alone hides the difference between two observations and two thousand. Return posterior variance with the updated mean. [PyMC, Beta distribution](https://www.pymc.io/projects/docs/en/stable/api/distributions/generated/pymc.Beta.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-betaupdate.git
cd blyx-betaupdate
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-betaupdate) · [Package page](https://www.blyx-lang.space/packages/betaupdate) · [Handbook](https://doc.blyx-lang.space/guide/redstart)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-betaupdate.git vendor/betaupdate
```

```blyx
use vendor::betaupdate::betaupdate;

fn main() {
    let alpha = 1.0;
    let beta = 1.0;
    let positive = 3.0;
    let negative = 1.0;
    let result = betaupdate_observe(alpha, beta, positive, negative);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
4
2
```

## API

`betaupdate_observe(alpha, beta, positive, negative)`

Returns [posterior alpha, posterior beta]. Use one count for each independent binary observation. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| alpha | A positive finite number |
| beta | A positive finite number |
| positive | A nonnegative exact integer |
| negative | A nonnegative exact integer |

## In use

[Redstart](https://github.com/Rahulchaube1/blyx-redstart) uses this module to update a binary-event model and report uncertainty in its probability.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-betaupdate/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
