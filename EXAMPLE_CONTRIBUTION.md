# Example Contribution: Adding LeakyReLU Activation Function

This is a **complete, working example** of how to add a new activation function to TensorFlow Playground. You can use this as a template for your own contributions.

## What is LeakyReLU?

LeakyReLU is an improved version of ReLU that allows a small gradient when the input is negative, preventing "dead neurons" during training.

**Formula**:
```
f(x) = x           if x > 0
f(x) = 0.01 * x    if x ≤ 0
```

**Derivative**:
```
f'(x) = 1      if x > 0
f'(x) = 0.01   if x ≤ 0
```

## Step-by-Step Implementation

### Step 1: Add the Activation Function to `src/nn.ts`

```typescript
// File: src/nn.ts
// Location: After line 136, inside the Activations class

export class Activations {
  public static TANH: ActivationFunction = {
    output: x => (Math as any).tanh(x),
    der: x => {
      let output = Activations.TANH.output(x);
      return 1 - output * output;
    }
  };
  public static RELU: ActivationFunction = {
    output: x => Math.max(0, x),
    der: x => x <= 0 ? 0 : 1
  };
  public static SIGMOID: ActivationFunction = {
    output: x => 1 / (1 + Math.exp(-x)),
    der: x => {
      let output = Activations.SIGMOID.output(x);
      return output * (1 - output);
    }
  };
  public static LINEAR: ActivationFunction = {
    output: x => x,
    der: x => 1
  };
  
  // ✅ ADD THIS NEW ACTIVATION FUNCTION
  public static LEAKY_RELU: ActivationFunction = {
    output: x => x > 0 ? x : 0.01 * x,
    der: x => x > 0 ? 1 : 0.01
  };
}
```

### Step 2: Register in State Management (`src/state.ts`)

```typescript
// File: src/state.ts
// Location: Around line 23, in the activations map

/** A map between names and activation functions. */
export let activations: {[key: string]: nn.ActivationFunction} = {
  "relu": nn.Activations.RELU,
  "tanh": nn.Activations.TANH,
  "sigmoid": nn.Activations.SIGMOID,
  "linear": nn.Activations.LINEAR,
  "leakyrelu": nn.Activations.LEAKY_RELU  // ✅ ADD THIS LINE
};
```

### Step 3: Add to UI Dropdown (`index.html`)

```html
<!-- File: index.html -->
<!-- Location: Around line 96, in the activations select element -->

<div class="control ui-activation">
  <label for="activations">Activation</label>
  <div class="select">
    <select id="activations">
      <option value="relu">ReLU</option>
      <option value="tanh">Tanh</option>
      <option value="sigmoid">Sigmoid</option>
      <option value="linear">Linear</option>
      <option value="leakyrelu">Leaky ReLU</option> <!-- ✅ ADD THIS LINE -->
    </select>
  </div>
</div>
```

## Testing Your Changes

### 1. Build the Project
```bash
npm run build
```

### 2. Start the Development Server
```bash
npm run serve-watch
```

### 3. Open in Browser
Navigate to http://localhost:3000

### 4. Test the New Activation Function

1. Select "Leaky ReLU" from the Activation dropdown
2. Try different datasets:
   - Circle dataset
   - XOR dataset
   - Spiral dataset
3. Click Play and observe:
   - Network should train successfully
   - Loss should decrease
   - Decision boundary should form correctly
4. Compare with ReLU to see the difference

### Expected Behavior

**Leaky ReLU vs ReLU**:
- Leaky ReLU should help prevent dead neurons
- May converge faster on some datasets
- Should handle negative gradients better

## Creating a Pull Request

### Commit Message
```bash
git add src/nn.ts src/state.ts index.html
git commit -m "Add LeakyReLU activation function

- Implements LeakyReLU with 0.01 slope for negative values
- Adds option to activation dropdown in UI
- Tested with all datasets (circle, XOR, spiral, gaussian)
- Helps prevent dead neuron problem compared to standard ReLU"
```

### Pull Request Template

```markdown
## Description
Adds LeakyReLU activation function as an alternative to standard ReLU.

## Motivation
LeakyReLU is a popular activation function that addresses the "dying ReLU" 
problem by allowing a small gradient when the unit is not active. This gives 
users another educational example to compare against standard ReLU.

## Changes
- Added `LEAKY_RELU` activation function to `src/nn.ts`
- Registered activation in state management (`src/state.ts`)
- Added UI option in activation dropdown (`index.html`)

## Testing
- ✅ Tested with Circle dataset - converges successfully
- ✅ Tested with XOR dataset - learns pattern correctly
- ✅ Tested with Spiral dataset - forms decision boundary
- ✅ Tested with Gaussian dataset - classifies correctly
- ✅ Verified URL state serialization works
- ✅ No console errors
- ✅ Builds successfully

## Screenshots
[Include a screenshot showing LeakyReLU working on spiral dataset]

## Additional Notes
Used alpha = 0.01 as the standard slope for negative values.
```

## Extending This Example

### Add Parameterized LeakyReLU

If you want to make the negative slope adjustable:

```typescript
// Create a factory function
export class Activations {
  // ... existing activations ...
  
  public static createLeakyReLU(alpha: number = 0.01): ActivationFunction {
    return {
      output: x => x > 0 ? x : alpha * x,
      der: x => x > 0 ? 1 : alpha
    };
  }
  
  public static LEAKY_RELU: ActivationFunction = 
    Activations.createLeakyReLU(0.01);
}
```

### Add Other ReLU Variants

Using the same pattern, you can add:

**PReLU (Parametric ReLU)**:
```typescript
public static PRELU: ActivationFunction = {
  output: x => x > 0 ? x : 0.25 * x,
  der: x => x > 0 ? 1 : 0.25
};
```

**ELU (Exponential Linear Unit)**:
```typescript
public static ELU: ActivationFunction = {
  output: x => x > 0 ? x : (Math.exp(x) - 1),
  der: x => x > 0 ? 1 : Math.exp(x)
};
```

**GELU (Gaussian Error Linear Unit)**:
```typescript
public static GELU: ActivationFunction = {
  output: x => {
    const sqrt2OverPi = Math.sqrt(2 / Math.PI);
    const cdf = 0.5 * (1 + Math.tanh(sqrt2OverPi * (x + 0.044715 * Math.pow(x, 3))));
    return x * cdf;
  },
  der: x => {
    // Approximate derivative
    const sqrt2OverPi = Math.sqrt(2 / Math.PI);
    const tanh_arg = sqrt2OverPi * (x + 0.044715 * Math.pow(x, 3));
    const sech2 = 1 - Math.pow(Math.tanh(tanh_arg), 2);
    return 0.5 * (1 + Math.tanh(tanh_arg)) + 
           x * 0.5 * sech2 * sqrt2OverPi * (1 + 3 * 0.044715 * Math.pow(x, 2));
  }
};
```

## Common Issues and Solutions

### Issue: Activation not appearing in dropdown
**Solution**: Make sure you've added it to all three files (nn.ts, state.ts, index.html)

### Issue: Network doesn't train
**Solution**: Check your derivative implementation - it should be correct mathematically

### Issue: NaN values during training
**Solution**: Your activation function might produce invalid values (infinity, NaN) for extreme inputs

### Issue: Build fails
**Solution**: Make sure TypeScript syntax is correct and you've rebuilt with `npm run build`

## Next Steps

After successfully implementing LeakyReLU, try:

1. **Add more activation functions** (ELU, SELU, Swish)
2. **Add optimizer variants** (Adam, RMSprop)
3. **Create new datasets** (half-moons, concentric circles)
4. **Add dropout visualization**
5. **Implement batch normalization**

---

**Good luck with your contribution! 🎉**

