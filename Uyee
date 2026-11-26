import os
from PIL import Image, ImageDraw, ImageFont

W, H = 1600, 2200
PAPER = '#f7f2e7'
INK = '#1a1a1a'
RED = '#c0392b'
BLUE = '#1f3a5f'
MUTED = '#55504a'
WHITE = '#ffffff'
GOLD = '#e5a32e'

image = Image.new('RGB', (W, H), PAPER)
draw = ImageDraw.Draw(image)

def get_font(size, bold=False):
    paths = ([
        '/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf',
        '/usr/share/fonts/truetype/liberation2/LiberationSans-Bold.ttf',
    ] if bold else [
        '/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf',
        '/usr/share/fonts/truetype/liberation2/LiberationSans-Regular.ttf',
    ])
    for path in paths:
        try:
            return ImageFont.truetype(path, size)
        except OSError:
            pass
    return ImageFont.load_default()

FONT_16 = get_font(16)
FONT_17 = get_font(17)
FONT_20B = get_font(20, True)
FONT_22B = get_font(22, True)
FONT_30B = get_font(30, True)
FONT_42B = get_font(42, True)
FONT_78B = get_font(78, True)

REGIONS = [
    ('EUROPE', '7 STORIES', [
        ('EU SUMMIT: 45BN EURO FOR KYIV', 'Leaders wrestle over 1.6tn euro budget and Ukraine loan.', 'gavel'),
        ('UKRAINE HITS RUSSIAN AIRBASE', '3 MiG-31s and 2 Su-34s damaged at Savasleyka.', 'flame'),
        ('RUSSIA LOST ABOUT 500,000 TROOPS', "Leaked data put Moscow's losses near half a million.", 'chart'),
        ('KYIV HIT BY BALLISTIC MISSILES', 'Shopping centre struck, 4 hurt in Russian retaliation.', 'flame'),
        ('MURMANSK GOVERNOR HELD', 'Regional chief in pre-trial detention on graft charges.', 'gavel'),
        ('UK CALLS UP 100,000 VETERANS', 'Ex-military asked to update details in huge exercise.', 'people'),
        ('SPAIN VOTES SUNDAY', 'Snap election looms with the right favoured to win.', 'ballot'),
    ]),
    ('ASIA-PACIFIC', '6 STORIES', [
        ('KIM ORDERS TACTICAL NUKES OUT', 'Deploy nuclear arms across domains, KCNA says.', 'rocket'),
        ('SHANGHAI PARTY CHIEF PROBED', "Chen Jining investigation shakes China's leadership.", 'gavel'),
        ('BANK OF KOREA HIKES TO 3.25%', 'Rate rise as prices stay under pressure.', 'chart'),
        ('MUMBAI MARKS 26/11, 18 YEARS ON', 'US envoy honours 166 victims of 2008 attacks.', 'candle'),
        ('INDIA FACES 25% US TARIFFS', 'Levy falls to 17% if Delhi signs a trade deal.', 'chart'),
        ('CHINA GOT NVIDIA CHIPS ANYWAY', 'Beijing beat US export rules, Reuters finds.', 'chip'),
    ]),
    ('MIDDLE EAST', '4 STORIES', [
        ('HOUTHIS HIT SAUDI PORTS', 'Jizan port struck; Ras Tanura refinery also targeted.', 'flame'),
        ('GAZA: HAMAS CHIEFS KILLED', 'Abu Nada slain overnight; Abu al-Ouf and family Wed.', 'flame'),
        ('US: LEAVE IRAN NOW', 'Washington warns citizens as war fears grow.', 'alert'),
        ("LEBANON'S SECOND AIRPORT", 'New northern airport opens next month.', 'plane'),
    ]),
    ('AFRICA', '4 STORIES', [
        ('CAIRO FIRE KILLS 31', 'Tanker inferno on ring road, 21 hurt, 27 vehicles charred.', 'flame'),
        ('CAIRO DRIVER DETAINED', 'Police hold driver blamed for the tanker crash.', 'gavel'),
        ('KENYA CULT LEADER CONVICTED', 'New charges for preacher serving 200 years.', 'gavel'),
        ('2,100 MIGRANTS IN A DAY', "Record arrivals reach Spain's Canary Islands.", 'boat'),
    ]),
    ('AMERICAS', '6 STORIES', [
        ('US TARIFFS HIT 14 PARTNERS', 'New levies on China, EU, Japan, India and more.', 'chart'),
        ("MACY'S PARADE MOVES TO SATURDAY", '100th parade postponed by storm, a first.', 'cloud'),
        ('BIRTHRIGHT ORDER BLOCKED', "Second judge halts Trump's citizenship curbs.", 'gavel'),
        ('FEDEX JET OVERSHOOTS IN MIAMI', 'MD-11 runs off runway; FAA grounds traffic.', 'plane'),
        ('NYC RENT FREEZE UPHELD', 'Judge backs freeze on about 1m stabilised flats.', 'home'),
        ('ECUADOR-US TALKS', 'Minister says talks focus on US operations in country.', 'handshake'),
    ]),
    ('MARKETS & TECH', '5 STORIES', [
        ('NASDAQ NEARS BEAR MARKET', 'AI sell-off: Nasdaq -0.62% to 23,586; S&P -0.21%.', 'chart'),
        ('FCC CLEARS 1M SPACEX SATELLITES', 'Starmind orbital data centres win first licence.', 'satellite'),
        ('HUANG BACK AMID US SCRUTINY', 'Nvidia chief returns as chip curbs face questions.', 'chip'),
        ('BRENT $91.19 ON HOUTHI FEARS', 'Oil +0.61% as Saudi attacks lift supply worries.', 'chart'),
        ('SPACEX +1.3% TO $127.44', 'Shares rise despite the wider tech rout.', 'rocket'),
    ]),
    ('SCIENCE & CULTURE', '3 STORIES', [
        ('LIVERPOOL WIN 3-0 IN BRUGGE', 'Reds cruise in the Champions League.', 'ball'),
        ('FALCONS TO GAIN 74% HABITAT', 'Warming could expand UK peregrine range by 2080.', 'leaf'),
        ('PHILLY PARADE CANCELLED', 'Thanksgiving parade called off as storm closes in.', 'cloud'),
    ]),
]

def draw_icon(kind, x, y, size=24):
    d = draw
    cx, cy = x + size // 2, y + size // 2
    if kind == 'flame':
        d.polygon([(cx, y), (x + size - 2, y + size * .45),
                   (cx + 3, y + size - 1), (x + 3, y + size * .67)], fill=RED)
        d.ellipse((cx - 4, cy + 1, cx + 4, y + size - 2), fill=GOLD)
    elif kind in ('gavel', 'chart'):
        if kind == 'gavel':
            d.line((x + 5, y + size - 4, x + size - 5, y + 5), fill=BLUE, width=4)
            d.line((x + 4, y + 5, x + 11, y + 12), fill=RED, width=5)
            d.line((x + 12, y - 1, x + 19, y + 6), fill=RED, width=5)
            d.line((x + 4, y + size - 2, x + size - 2, y + size - 2), fill=INK, width=3)
        else:
            d.line((x + 3, y + size - 3, x + 3, y + 4), fill=BLUE, width=2)
            d.line((x + 3, y + size - 3, x + size - 1, y + size - 3), fill=BLUE, width=2)
            d.line((x + 5, y + size - 7, x + 10, y + size - 13, x + 14, y + size - 11, x + 21, y + 3), fill=RED, width=3)
            d.polygon([(x + 17, y + 3), (x + 22, y + 2), (x + 21, y + 8)], fill=RED)
    elif kind in ('rocket', 'satellite'):
        d.ellipse((x + 7, y + 1, x + size - 5, y + size - 7), fill=RED)
        d.polygon([(cx, y - 1), (x + 4, y + 10), (x + size - 4, y + 10)], fill=RED)
        d.ellipse((cx - 3, y + 7, cx + 3, y + 13), fill=WHITE)
        d.polygon([(x + 8, y + size - 10), (x + 2, y + size - 2), (x + 11, y + size - 5)], fill=BLUE)
        d.polygon([(x + size - 8, y + size - 10), (x + size - 2, y + size - 2), (x + size - 11, y + size - 5)], fill=BLUE)
        if kind == 'satellite':
            d.line((x + 1, cy, x + size - 1, cy), fill=BLUE, width=2)
    elif kind in ('people', 'ballot', 'candle', 'chip', 'alert', 'plane', 'boat', 'home', 'handshake', 'cloud', 'leaf', 'ball'):
        if kind == 'people':
            for px in (x + 4, x + 14):
                d.ellipse((px, y + 2, px + 7, y + 9), fill=BLUE)
                d.arc((px - 2, y + 8, px + 10, y + 23), 180, 360, fill=RED, width=4)
        elif kind == 'ballot':
            d.rectangle((x + 3, y + 4, x + size - 3, y + size - 2), outline=BLUE, width=2)
            d.line((x + 7, y + 9, x + size - 7, y + 9), fill=RED, width=2)
            d.line((x + 8, y + 3, x + 11, y + 7, x + 19, y - 1), fill=RED, width=2)
        elif kind == 'candle':
            d.rectangle((cx - 4, y + 8, cx + 4, y + size - 1), fill=BLUE)
            d.ellipse((cx - 4, y + 1, cx + 4, y + 10), fill=GOLD)
        elif kind == 'chip':
            d.rectangle((x + 5, y + 5, x + size - 5, y + size - 5), fill=BLUE)
            for p in (7, 13, 19):
                d.line((x + p, y + 1, x + p, y + 5), fill=RED, width=2)
                d.line((x + p, y + size - 5, x + p, y + size - 1), fill=RED, width=2)
                d.line((x + 1, y + p, x + 5, y + p), fill=RED, width=2)
                d.line((x + size - 5, y + p, x + size - 1, y + p), fill=RED, width=2)
        elif kind == 'alert':
            d.polygon([(cx, y + 1), (x + size - 1, y + size - 2), (x + 1, y + size - 2)], fill=GOLD)
            d.line((cx, y + 7, cx, y + 15), fill=INK, width=3)
            d.ellipse((cx - 1, y + 17, cx + 1, y + 19), fill=INK)
        elif kind == 'plane':
            d.polygon([(x + 1, cy - 2), (x + 9, cy - 4), (cx, y + 2), (x + 15, cy - 4), (x + size - 1, cy - 2), (x + 16, cy + 2), (x + 14, y + size - 2), (cx, cy + 5), (x + 8, y + size - 2), (x + 8, cy + 1)], fill=BLUE)
        elif kind == 'boat':
            d.polygon([(x + 2, y + 14), (x + size - 2, y + 14), (x + size - 6, y + 20), (x + 6, y + 20)], fill=BLUE)
            d.line((cx, y + 2, cx, y + 14), fill=RED, width=2)
            d.polygon([(cx - 1, y + 3), (cx - 1, y + 12), (x + size - 3, y + 12)], fill=GOLD)
        elif kind == 'home':
            d.polygon([(x + 1, y + 11), (cx, y + 2), (x + size - 1, y + 11)], fill=RED)
            d.rectangle((x + 4, y + 10, x + size - 4, y + size - 1), fill=BLUE)
            d.rectangle((cx - 2, y + 14, cx + 2, y + size - 1), fill=PAPER)
        elif kind == 'handshake':
            d.line((x + 2, y + 9, x + 8, y + 5, x + 13, y + 9, x + 18, y + 5, x + 22, y + 9), fill=BLUE, width=4)
            d.line((x + 4, y + 11, x + 11, y + 18, x + 14, y + 15, x + 17, y + 18, x + 21, y + 12), fill=RED, width=3)
        elif kind == 'cloud':
            d.ellipse((x + 2, y + 9, x + 13, y + 20), fill=BLUE)
            d.ellipse((x + 8, y + 4, x + 19, y + 20), fill=BLUE)
            d.ellipse((x + 13, y + 9, x + 23, y + 20), fill=BLUE)
            d.rectangle((x + 7, y + 13, x + 19, y + 20), fill=BLUE)
            d.line((x + 5, y + 22, x + 3, y + 24), fill=RED, width=2)
            d.line((x + 15, y + 22, x + 13, y + 24), fill=RED, width=2)
        elif kind == 'leaf':
            d.ellipse((x + 4, y + 2, x + 21, y + 20), fill='#557c45')
            d.line((x + 5, y + 21, x + 17, y + 7), fill=WHITE, width=2)
        else:
            d.ellipse((x + 3, y + 3, x + size - 3, y + size - 3), fill=RED)
            d.line((cx, y + 4, cx, y + size - 4), fill=WHITE, width=2)
            d.arc((x + 6, y + 5, x + size - 6, y + size - 5), 80, 280, fill=WHITE, width=2)

def fit_text(text, font, max_width):
    if draw.textlength(text, font=font) <= max_width:
        return text
    shortened = text
    while shortened and draw.textlength(shortened + '...', font=font) > max_width:
        shortened = shortened[:-1]
    return shortened.rstrip(' -:') + '...'

def draw_story(x, y, width, headline, detail, icon, row_height):
    draw_icon(icon, x, y + 7, 24)
    text_x = x + 34
    text_width = width - 36
    h = fit_text(headline, FONT_20B, text_width)
    detail_line = fit_text(detail, FONT_16, text_width)
    draw.text((text_x, y), h, font=FONT_20B, fill=INK)
    draw.text((text_x, y + 23), detail_line, font=FONT_16, fill=MUTED)
    draw.line((x, y + row_height - 2, x + width, y + row_height - 2), fill='#d9d1c4', width=1)

def draw_region(x, y, width, height, region):
    name, count, stories = region
    bar_h = 36
    draw.rectangle((x, y, x + width, y + bar_h), fill=BLUE)
    draw.text((x + 12, y + 5), name, font=FONT_22B, fill=WHITE)
    count_width = draw.textlength(count, font=FONT_16)
    draw.text((x + width - count_width - 12, y + 10), count, font=FONT_16, fill=WHITE)
    content_h = height - bar_h
    row_h = content_h / len(stories)
    for i, story in enumerate(stories):
        draw_story(x + 8, y + bar_h + i * row_h + 2, width - 16, *story, row_h)

def draw_masthead():
    draw.text((48, 22), 'THE WORLD IN ONE DAY', font=FONT_78B, fill=INK)
    draw.text((54, 119), 'Thursday, 26 November 2026', font=FONT_30B, fill=INK)
    meta = '35 STORIES  |  7 REGIONS'
    draw.text((W - 52 - draw.textlength(meta, font=FONT_22B), 130), meta, font=FONT_22B, fill=BLUE)
    draw.rectangle((48, 174, W - 48, 181), fill=RED)

def draw_hero():
    x, y, w, h = 48, 195, 1504, 440
    scene_w = 590
    draw.rectangle((x, y, x + w, y + h), fill='#eee7d9', outline=RED, width=3)
    draw.rectangle((x + 2, y + 2, x + scene_w, y + h - 2), fill='#302c29')
    # smoke columns and drifting soot
    for box, color in [
        ((x + 180, y + 34, x + 333, y + 183), '#55514c'),
        ((x + 260, y + 11, x + 431, y + 170), '#494540'),
        ((x + 345, y + 48, x + 514, y + 189), '#605a52'),
        ((x + 114, y + 81, x + 263, y + 195), '#4b4742'),
        ((x + 400, y + 7, x + 527, y + 125), '#514c47'),
    ]:
        draw.ellipse(box, fill=color)
    for sx, sy, radius in [(195, 40, 8), (415, 59, 6), (298, 20, 5), (488, 104, 7), (155, 124, 5)]:
        draw.ellipse((x + sx - radius, y + sy - radius, x + sx + radius, y + sy + radius), fill='#81796e')
    # tall flames behind the tanker
    flame_shapes = [
        [(105, 282), (117, 215), (133, 246), (150, 165), (169, 244), (190, 190), (209, 281)],
        [(190, 282), (207, 203), (226, 237), (244, 147), (261, 237), (281, 181), (298, 282)],
        [(300, 282), (317, 212), (334, 241), (350, 162), (370, 244), (390, 195), (414, 282)],
        [(392, 282), (410, 220), (429, 249), (451, 179), (468, 241), (487, 207), (514, 282)],
    ]
    for points in flame_shapes:
        draw.polygon([(x + px, y + py) for px, py in points], fill='#d94b23')
        inner = [(points[0][0] + 12, points[0][1]), (points[1][0] + 10, points[1][1] + 27),
                 (points[2][0] + 5, points[2][1] + 3), (points[3][0] + 3, points[3][1] + 33),
                 (points[4][0], points[4][1] + 1), (points[5][0] - 7, points[5][1] + 28),
                 (points[6][0] - 8, points[6][1])]
        draw.polygon([(x + px, y + py) for px, py in inner], fill=GOLD)
    # ring road and lane markings
    draw.polygon([(x + 2, y + 316), (x + scene_w - 2, y + 289),
                  (x + scene_w - 2, y + h - 2), (x + 2, y + h - 2)], fill='#44413c')
    draw.line((x + 10, y + 369, x + scene_w - 4, y + 344), fill='#d3c7ac', width=4)
    for px in (135, 259, 385, 512):
        draw.line((x + px, y + 376 - px // 30, x + px + 42, y + 374 - px // 30), fill='#e8dfca', width=4)
    # overturned tanker and cab
    draw.rounded_rectangle((x + 154, y + 272, x + 410, y + 336), radius=22, fill='#b9b09d', outline='#171615', width=4)
    draw.rectangle((x + 175, y + 280, x + 390, y + 290), fill='#d3cbb9')
    draw.line((x + 177, y + 304, x + 391, y + 304), fill='#7d766a', width=2)
    draw.rectangle((x + 409, y + 294, x + 486, y + 339), fill=RED, outline='#171615', width=3)
    draw.polygon([(x + 426, y + 294), (x + 468, y + 294), (x + 481, y + 312), (x + 421, y + 312)], fill='#8eb1b7')
    for wx in (x + 192, x + 328, x + 433, x + 472):
        draw.ellipse((wx - 14, y + 322, wx + 14, y + 350), fill='#171615')
        draw.ellipse((wx - 6, y + 330, wx + 6, y + 342), fill='#8c8578')
    # charred cars at the roadside
    for cx, cy in [(45, 336), (500, 351)]:
        draw.rounded_rectangle((x + cx, y + cy, x + cx + 83, y + cy + 31), radius=7, fill='#201f1d', outline='#100f0e', width=2)
        draw.polygon([(x + cx + 15, y + cy), (x + cx + 29, y + cy - 13),
                      (x + cx + 61, y + cy - 13), (x + cx + 72, y + cy)], fill='#292725')
        draw.ellipse((x + cx + 12, y + cy + 23, x + cx + 31, y + cy + 42), fill='#100f0e')
        draw.ellipse((x + cx + 56, y + cy + 23, x + cx + 75, y + cy + 42), fill='#100f0e')
    # headline and readable summary
    tx = x + scene_w + 38
    text_w = w - scene_w - 68
    draw.text((tx, y + 28), 'BREAKING  /  EGYPT', font=FONT_20B, fill=RED)
    draw.text((tx, y + 66), 'CAIRO RING ROAD', font=FONT_42B, fill=INK)
    draw.text((tx, y + 117), 'INFERNO - 31 DEAD', font=FONT_42B, fill=INK)
    draw.rectangle((tx, y + 180, tx + 96, y + 186), fill=RED)
    sub = ('Fuel tanker overturns in Warraq and bursts into flames, '
           'torching 27 vehicles. Health ministry toll is preliminary - 21 hurt.')
    words, lines, line = sub.split(), [], ''
    for word in words:
        candidate = (line + ' ' + word).strip()
        if draw.textlength(candidate, font=FONT_22B) > text_w:
            lines.append(line)
            line = word
        else:
            line = candidate
    if line:
        lines.append(line)
    for i, line in enumerate(lines[:4]):
        draw.text((tx, y + 207 + i * 34), line, font=FONT_22B, fill=INK)
    draw.text((tx, y + h - 50), 'WARRAQ RING ROAD  |  PRELIMINARY TOLL', font=FONT_16, fill=MUTED)

def draw_footer():
    y = 2074
    draw.rectangle((48, y, W - 48, y + 92), fill='#e9e1d3')
    draw.rectangle((48, y, W - 48, y + 4), fill=RED)
    try:
        italic = ImageFont.truetype('/usr/share/fonts/truetype/dejavu/DejaVuSans-Oblique.ttf', 17)
    except OSError:
        italic = FONT_17
    footer = "THANKSGIVING IN THE STORM - Macy's 100th parade moves to Saturday as heavy rain and wind hit New York."
    draw.text((64, y + 17), fit_text(footer, italic, W - 128), font=italic, fill=INK)
    draw.text((64, y + 54), 'Sources: wire reports and official statements, 26 November 2026.', font=FONT_16, fill=MUTED)

def main():
    draw_masthead()
    draw_hero()
    left, right, gap = 48, 810, 28
    col_w = 742
    draw_region(left, 656, col_w, 410, REGIONS[0])
    draw_region(right, 656, col_w, 410, REGIONS[1])
    draw_region(left, 1080, col_w, 292, REGIONS[2])
    draw_region(right, 1080, col_w, 292, REGIONS[3])
    draw_region(left, 1386, col_w, 370, REGIONS[4])
    draw_region(right, 1386, col_w, 370, REGIONS[5])
    draw_region(48, 1770, W - 96, 190, REGIONS[6])
    draw_footer()
    out_dir = os.environ.get('MAKEFUN_OUTPUT_DIR', '/output')
    os.makedirs(out_dir, exist_ok=True)
    out_path = os.path.join(out_dir, 'entry.png')
    image.save(out_path, format='PNG', optimize=False)
    print('Image size:', image.size)
    print('File size:', os.path.getsize(out_path), 'bytes')

if __name__ == '__main__':
    main()
