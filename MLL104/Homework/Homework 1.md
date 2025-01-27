### Plot the black body radiation spectrum for temperatures T = 273K, 500K, 2000K, 5000K. which one will you use for IR spectrometer and why ?
```
import numpy as np
import matplotlib.pyplot as plt

# Constants
h = 6.626e-34  # Planck's constant (J·s)
c = 3e8        # Speed of light (m/s)
k_B = 1.381e-23 # Boltzmann constant (J/K)

def planck_wavelength(wavelength, temperature):
    """Calculate spectral radiance using Planck's law (wavelength form)."""
    wavelength_m = wavelength * 1e-9  # Convert nm to meters
    term1 = (2 * h * c**2) / (wavelength_m**5)
    term2 = 1 / (np.exp((h * c) / (wavelength_m * k_B * temperature)) - 1)
    return term1 * term2

# Wavelength range (in nanometers)
wavelengths = np.linspace(1, 3000, 1000)  # 1 nm to 3000 nm

# Temperatures
temperatures = [273, 500, 2000, 5000]

# Plot the spectra
plt.figure(figsize=(10, 6))
for T in temperatures:
    radiance = planck_wavelength(wavelengths, T)
    # Normalize radiance for relative comparison
    radiance_normalized = radiance / np.max(radiance)
    plt.plot(wavelengths, radiance_normalized, label=f"T = {T} K")

# Add labels and legend
plt.title("Black Body Radiation Spectrum (Wavelength Form)")
plt.xlabel("Wavelength (nm)")
plt.ylabel("Relative Spectral Radiance (Arbitrary Units)")
plt.legend()
plt.grid(True)
plt.show()

```

![[spectral radiation.png]]
answer maybe 400




### Look up Airy functions. Plot it with a software. These functions are solutions to a known differential equation. Can you describe that equation ? [2]
Airy functions are named after the English astronomer George Biddell Airy
(1801–1892).
The name Airy is connected with many
physical phenomena and includes, besides the Airy disk, the Airy spiral, an
optical phenomenon visible on quartz crystals, and the Airy stress function in
elasticity.
The Airy functions Ai(_x_) and Bi(_x_) are the two linearly independent solutions of the differential equation

∂2y∂x2−xy=0.

Ai(_x_) is called the Airy function of the first kind. Bi(_x_) is called the Airy function of the second kind.

```
import numpy as np
import matplotlib.pyplot as plt
from scipy.special import airy

# Define the range of x values
x = np.linspace(-10, 10, 400)

# Calculate the Airy function values
Ai, Bi = airy(x)

# Plotting the Airy functions
plt.figure(figsize=(8, 6))
plt.plot(x, Ai, label='Ai(x)', color='blue')
plt.plot(x, Bi, label='Bi(x)', color='red')
plt.title('Airy Functions Ai(x) and Bi(x)')
plt.xlabel('x')
plt.ylabel('Function value')
plt.legend()
plt.grid(True)
plt.show()

```
![[airy.png]]

### What is a diffraction grating ? How is wavelength separation achieved using such a structure and what is the physical requirement for the spectrometer using diffraction gratings [2]

A differential grating is an optical grating with varying groove spacing or material properties across its surface. This variation causes different diffraction angles for different wavelengths or positions, offering enhanced control over the diffraction process.
##### Wavelength Separation Using a Differential Grating Structure

Wavelength separation using a differential grating structure is achieved by introducing a spatial variation in the grating period (the distance between grooves or lines), which causes the diffraction angle to depend not only on the wavelength of light but also on the position on the grating's surface. This creates a non-uniform diffraction pattern, enabling better separation of wavelengths, particularly in cases where high resolution or separation of closely spaced spectral lines is required.

In a traditional diffraction grating, the diffraction angle $\theta$ is given by the grating equation:

$$
m\lambda = d \sin \theta
$$

where:
- $m$ is the diffraction order,
- $\lambda$ is the wavelength,
- $d$ is the grating spacing.

However, in a differential grating, the spacing $d(x)$ is a function of position $x$, so the diffraction angle becomes position-dependent. This means that each wavelength is diffracted differently at different positions along the grating, allowing for enhanced wavelength separation by resolving smaller differences in wavelength.

###### Physical Requirements for a Spectrometer Using Diffraction Gratings

For a spectrometer using diffraction gratings, the key physical requirements include:

1. **High Spatial Resolution**:  
   To achieve precise wavelength separation, the spectrometer must be able to detect fine variations in the diffraction pattern produced by the grating.

2. **Grating Period Control**:  
   The grating must have a carefully engineered period (or modulation) that varies with position to achieve the differential diffraction effect. This modulation must be smooth and predictable to ensure effective wavelength separation.

3. **Wide Angular Range**:  
   The spectrometer must have a detector capable of measuring the angular dispersion of light across a wide range of angles to capture the separated wavelengths effectively.

4. **Optical Coherence**:  
   For high-resolution spectrometry, the light source should have a narrow spectral bandwidth, ensuring that the separation of wavelengths produced by the grating is distinct and measurable.

5. **Material and Geometry**:  
   The choice of material and the geometric configuration of the grating are also critical to maintain efficiency and minimize losses. The grating's design must minimize scattering and maximize diffraction efficiency.

### How are the following similar and different?[4] a. 𝜎 molecular orbital and 𝜋 molecular orbitals b. Bonding and non bonding orbitals


#### a. 𝜎 Molecular Orbitals vs. 𝜋 Molecular Orbitals

**Similarities:**

- Both 𝜎 and 𝜋 molecular orbitals are formed from the linear combination of atomic orbitals (LCAO) in the context of molecular orbital theory.
- Both types of orbitals represent the spatial distribution of electrons in a molecule, and their shapes and energies are determined by the combination of the atomic orbitals of the constituent atoms.
- Both can be bonding or antibonding, depending on whether the wavefunctions of the atomic orbitals combine constructively or destructively.

**Differences:**

- **Symmetry**: The key distinction lies in their symmetry relative to the internuclear axis (the line joining the nuclei of the bonding atoms).
    
    - **𝜎 Molecular Orbitals**: These orbitals are formed by the end-to-end (head-on) overlap of atomic orbitals. This overlap is along the internuclear axis, and the electron density is symmetrically distributed around this axis.
        - Example: The combination of two atomic 1s orbitals to form a 𝜎 bonding orbital.
    - **𝜋 Molecular Orbitals**: These orbitals arise from the sideways overlap of atomic orbitals (usually p orbitals). The electron density is above and below the internuclear axis, rather than along it.
        - Example: The combination of two p orbitals from each atom to form a 𝜋 bonding orbital.
- **Bond Strength**:
    
    - 𝜎 bonds are typically stronger than 𝜋 bonds due to the greater extent of overlap of the atomic orbitals. The electron density in 𝜎 bonds is more concentrated along the internuclear axis, creating a stronger bond.
    - 𝜋 bonds, due to their sideways overlap, generally have a weaker bonding interaction compared to 𝜎 bonds, as the overlap is less effective.
- **Formation and Bonding**:
    
    - 𝜎 orbitals can form single bonds and also contribute to higher-order bonds in molecules (e.g., in triple bonds, where there is one 𝜎 and two 𝜋 bonds).
    - 𝜋 orbitals, on the other hand, typically form part of a multiple bond, such as in double or triple bonds (e.g., a carbon-carbon double bond involves one 𝜎 bond and one 𝜋 bond).

#### b. Bonding Orbitals vs. Non-Bonding Orbitals

**Similarities:**

- Both bonding and non-bonding orbitals are derived from the molecular orbital theory, and both describe the spatial distribution of electrons in a molecule.
- Both contribute to the total molecular energy and influence the molecule's properties.

**Differences:**

- **Bonding Orbitals**:
    
    - Bonding orbitals are formed when atomic orbitals combine constructively, meaning the wavefunctions of the contributing orbitals are in phase. This leads to an increase in electron density between the nuclei, resulting in a stabilizing effect and a lower energy state for the molecule.
    - These orbitals are responsible for holding the atoms together and stabilizing the molecule. In a diatomic molecule, bonding orbitals are typically occupied first in the molecular orbital diagram.
    - Example: A 𝜎 bonding orbital formed by the constructive overlap of two 1s orbitals.
- **Non-Bonding Orbitals**:
    
    - Non-bonding orbitals are formed when atomic orbitals combine in such a way that the overlap is neither constructive nor destructive. The electron density in these orbitals does not significantly contribute to bonding or antibonding interactions.
    - These orbitals are typically occupied by electrons in atoms where their energy is approximately the same as the atomic orbital energy, and they do not play a role in the overall bond strength. Non-bonding orbitals are essentially “isolated” in the sense that they do not favor bond formation or breakage.
    - Example: The p-orbitals on a lone atom in a molecule, such as the lone pair electrons in a water molecule.
- **Impact on Molecular Properties**:
    
    - Electrons in bonding orbitals contribute to the stability and strength of the molecule, while electrons in non-bonding orbitals do not affect the bonding but can influence other properties such as polarity, reactivity, and the overall electron distribution in the molecule.

To summarize:

- **𝜎 vs. 𝜋 Orbitals**: 𝜎 orbitals involve end-to-end overlap and are stronger, while 𝜋 orbitals involve sideways overlap and are typically weaker.
- **Bonding vs. Non-Bonding Orbitals**: Bonding orbitals stabilize the molecule, while non-bonding orbitals do not contribute directly to bonding or antibonding interactions.

#### a. 𝜎 Molecular Orbitals vs. 𝜋 Molecular Orbitals: Advanced Theoretical Framework

#### Symmetry and Molecular Orbital Theory (MO Theory)

In molecular orbital theory, the fundamental premise is that the electronic structure of a molecule can be described by molecular orbitals, which are linear combinations of atomic orbitals. When considering 𝜎 and 𝜋 orbitals, we invoke group theory and the concept of symmetry-adapted linear combinations (SALCs) to describe their formation.

- **𝜎 Molecular Orbitals**: These are formed by the head-on (end-to-end) overlap of atomic orbitals, typically from s or p orbitals. From a group theory perspective, the combination of orbitals must belong to the same irreducible representation (IR), and the 𝜎 orbitals are the result of symmetric combinations. These combinations maintain the symmetry of the molecular axis, resulting in electron density along the internuclear axis.
    
    - In terms of symmetry-adapted orbitals, the 𝜎 orbital will correspond to the symmetric representation of the group, and the energy of these orbitals will be lower because of the constructive interference of the electron wavefunctions.
- **𝜋 Molecular Orbitals**: These orbitals are formed by the lateral (side-by-side) overlap of atomic orbitals, usually from p orbitals. From a group theoretical perspective, the combination of p orbitals on two atoms must lead to a molecular orbital with an antisymmetric wavefunction with respect to rotation around the internuclear axis. These orbitals will transform according to a different irreducible representation than 𝜎 orbitals. The key feature of 𝜋 orbitals is the nodal plane along the internuclear axis, which means there is no electron density directly between the nuclei, resulting in a weaker overlap and generally weaker bonding.
    
    - The 𝜋 molecular orbital is typically higher in energy than the corresponding 𝜎 orbital due to less effective overlap and a higher degree of angular nodal features that lead to less stabilization.

#### Electronic Coupling and Bonding

From the perspective of **electronic coupling** and **orbital interactions**, 𝜎 orbitals exhibit stronger bonding due to the more effective overlap along the internuclear axis. This overlap leads to a greater **overlap integral (S)**, which quantifies the extent to which two wavefunctions overlap spatially. The stronger overlap in 𝜎 orbitals results in a lower energy of the bonding molecular orbital and a stronger bond.

In contrast, 𝜋 orbitals have a reduced overlap integral due to the lateral nature of the interaction. This weaker coupling leads to a **less stabilized molecular orbital** with relatively higher energy.

#### Orbital Hybridization and Bonding

Advanced theories, such as **valence bond theory** with hybridization, describe bonding in terms of the hybridization of atomic orbitals to form the bonding molecular orbitals. For 𝜎 bonds, hybridization is often sp³, sp², or sp, where atomic orbitals mix to create orbitals with directional character along the internuclear axis. In contrast, 𝜋 bonds arise from the lateral overlap of unhybridized p orbitals in sp² and sp hybridized systems.

#### b. Bonding Orbitals vs. Non-Bonding Orbitals: Advanced Quantum Mechanical Considerations

#### Bonding Orbitals: Molecular Stabilization in Terms of Electron Density

Bonding orbitals, from a quantum mechanical standpoint, are characterized by **constructive interference** between the wavefunctions of the atomic orbitals. This constructive interference leads to a **decrease in molecular energy** due to an increase in electron density between the nuclei, resulting in a net stabilizing effect on the molecule. The molecular orbital formed is characterized by a higher electron density in the region between the atoms, which results in the lowering of the energy of the entire system.

- In a bonding orbital, the **electron density distribution** exhibits constructive overlap, reducing the energy of the system compared to the energy of the isolated atomic orbitals.

#### Non-Bonding Orbitals: The Role of Orbital Energy and Electron Localization

Non-bonding orbitals do not significantly contribute to the bonding interaction. These orbitals result from atomic orbitals that do not mix constructively or destructively in the molecular orbital approach. Non-bonding orbitals are often **localized on a single atom** or involve orbitals that have no effective interaction with other atomic orbitals in the molecule. They are not part of the bonding or antibonding interactions but still play a role in the total electronic energy of the molecule.

From an advanced perspective, **non-bonding orbitals**:

- Exist when atomic orbitals, often in the case of lone pairs or degenerate orbitals, do not have a favorable overlap with orbitals from neighboring atoms.
- Retain an energy similar to that of the original atomic orbital because they don’t contribute to bonding or antibonding effects. Hence, they are said to "occupy a non-bonding molecular orbital," which remains essentially at the energy of the atomic orbital from which it originates.

In **extended conjugation** (such as in aromatic compounds), non-bonding orbitals often serve as **reactive sites** for nucleophilic or electrophilic attack, influencing the chemical reactivity of the molecule.

#### Impact on Molecular Reactivity: Frontier Molecular Orbital Theory

In the context of **Frontier Molecular Orbital (FMO) theory**, bonding and non-bonding orbitals play crucial roles in determining the reactivity of molecules. Bonding orbitals stabilize a molecule, while non-bonding orbitals often serve as the **reactive frontier**.

- **FMO theory** explains that reactions occur when the **highest occupied molecular orbital (HOMO)** of one molecule interacts with the **lowest unoccupied molecular orbital (LUMO)** of another molecule. Non-bonding orbitals may contribute to the HOMO in the form of lone pairs or unreactive electron distributions, making them important in processes like **nucleophilic attack**.

Thus, non-bonding orbitals, despite not contributing directly to bonding interactions, can **modulate molecular reactivity** by providing potential sites for chemical interactions.

#### Conclusion:

- **𝜎 vs. 𝜋 Molecular Orbitals**: The advanced quantum mechanical treatment highlights the differences in symmetry, energy levels, and overlap integrals between 𝜎 and 𝜋 orbitals. 𝜎 orbitals have stronger bonding due to more effective overlap, while 𝜋 orbitals, formed from sideways overlap, generally lead to weaker bonding interactions.
- **Bonding vs. Non-Bonding Orbitals**: Bonding orbitals lower the overall energy of a molecule by concentrating electron density between the nuclei, while non-bonding orbitals do not contribute to this stabilization and are often localized, influencing reactivity rather than stability.

These advanced theories, including group theory, electronic coupling, hybridization, and FMO theory, provide a more nuanced and comprehensive understanding of molecular interactions.

### In the traditional FTIR interferometer, Assuming the light to be a plane wave of form 𝜓 = 𝐴𝑒 !"# , find the sum of light from two paths: one path has a tunable delay of 𝛿. Remember to assume mirrors do not introduce change in phase (in reality, they add 180 phase shift, but since the phase shift is common to both the paths, it does not affect our calculations. )
#### FTIR Interferometer: Sum of Light from Two Paths with Tunable Delay

In the traditional FTIR interferometer, we consider two paths with one path having a tunable delay ( $\delta$ ). We assume that the light in both paths is a plane wave and that the mirrors do not introduce any additional phase shifts, which simplifies the calculation.

#### 1. **Plane Wave Representation**
The light in both paths can be represented as a plane wave of the form:

$$
\psi = A e^{i(kx - \omega t)}
$$

where:
- \( A \) is the amplitude of the wave,
- \( k = $\frac{2\pi}{\lambda}$ \) is the wave number,
- \( $\omega = 2\pi f$ \) is the angular frequency,
- \( x \) is the spatial position, and
- $( t )$ is the time.

#### 2. **Light in the First Path (No Delay)**
For the path without any delay, the wave remains unchanged and is given by:

$$
\psi_1 = A e^{i(kx - \omega t)}
$$

#### 3. **Light in the Second Path (With Delay \( $\delta$ \))**
For the path with the tunable delay \( \delta \), the wave acquires a phase shift due to the difference in path length. The light in this path can be written as:

$$
\psi_2 = A e^{i(k(x + \delta) - \omega t)} = A e^{i(kx - \omega t)} e^{i k \delta}
$$

Here, \( $e^{i k \delta}$ \) introduces a phase shift dependent on the path delay \( \delta \).

#### 4. **Summing the Two Waves**
The total wave after both paths combine is simply the sum of \( \psi_1 \) and \( \psi_2 \):

$$
\psi_{\text{total}} = \psi_1 + \psi_2 = A e^{i(kx - \omega t)} + A e^{i(kx - \omega t)} e^{i k \delta}
$$

Factoring out the common terms, we get:

$$
\psi_{\text{total}} = A e^{i(kx - \omega t)} \left(1 + e^{i k \delta}\right)
$$

#### 5. **Simplifying the Expression**
We use the identity for the sum of complex exponentials:

$$
1 + e^{i k \delta} = 2 \cos\left(\frac{k \delta}{2}\right) e^{i \frac{k \delta}{2}}
$$

Thus, the total wave becomes:

$$
\psi_{\text{total}} = A e^{i(kx - \omega t)} \cdot 2 \cos\left(\frac{k \delta}{2}\right) e^{i \frac{k \delta}{2}}
$$

#### 6. **Final Expression for Total Light**
The total light can now be expressed as:

$$
\psi_{\text{total}} = 2 A \cos\left(\frac{k \delta}{2}\right) e^{i(kx - \omega t + \frac{k \delta}{2})}
$$

This represents the light after combining the two paths, with the interference pattern determined by the term \( $\cos\left(\frac{k \delta}{2}\right)$ \), which depends on the path delay \( \delta \).

#### 7. **Intensity of the Total Light**
The intensity of the light is proportional to the square of the magnitude of the total wave:

$$
I_{\text{total}} \propto \left| 2 A \cos\left(\frac{k \delta}{2}\right) \right|^2
$$

Thus, the intensity as a function of delay \( \delta \) is:

$$
I_{\text{total}} \propto 4 A^2 \cos^2\left(\frac{k \delta}{2}\right)
$$

This expression describes the interference pattern observed in the FTIR setup, where the intensity varies as the cosine of half the path delay.
