[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

    import math
    import nsfg

    df = nsfg.ReadFemPreg()
    df['totalwgt_lb'] = df.birthwgt_lb + df.birthwgt_oz / 16.0

    live = df[df.outcome == 1]
    firsts = live[live.birthord == 1]
    others = live[live.birthord != 1]

    first_weight = firsts.totalwgt_lb
    other_weight = others.totalwgt_lb

    first_preglength = firsts.prglngth
    other_preglength = others.prglngth


    def CohenEffectSize(group1, group2):
        diff = group1.mean() - group2.mean()

        var1 = group1.var()
        var2 = group2.var()
        n1, n2 = len(group1), len(group2)
        pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)

        d = diff / math.sqrt(pooled_var)
        return d


    print(CohenEffectSize(first_weight, other_weight))
    print(CohenEffectSize(first_preglength, other_preglength))

This returns

    -0.088672927072602
    0.028879044654449883
    
